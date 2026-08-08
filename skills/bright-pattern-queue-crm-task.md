---
name: Queue a CRM task into Bright Pattern and track it to completion
description: Authenticate against a Bright Pattern tenant, queue a task from an external CRM with de-duplicating external identifiers, then query, update or cancel it.
api: openapi/bright-pattern-task-routing-openapi.yml
operations: [getAccessToken, queueTask, queryTask, updateTask, cancelTask, cancelServiceTasks]
generated: '2026-08-08'
method: generated
---

# Queue a CRM task into Bright Pattern

Use the Task Routing API to push work from an external system (CRM, ticketing, workflow engine) into a
Bright Pattern contact center so it is routed to an agent.

## Before you start

- Bright Pattern is **multi-tenant**. Every request goes to your contact center's own hostname,
  `https://<tenant>.brightpattern.com`. There is no shared production host.
- The API client must authenticate as a contact-center user whose role holds the
  **Use Task Routing API** privilege. Without it every call fails `403` with application error code `3`.

## 1. Get an access token

Call `getAccessToken` — `POST /configapi/v2/oauth/token` — with an OAuth 2.0 `client_credentials` grant
using the integration account's client id and client secret. Send the returned token as
`Authorization: Bearer <access_token>` on every other call.

Tokens expire. Application error code `2` ("Access token expired", HTTP `401`) means request a new one
and retry; code `1` means the header is missing or the token never existed — do not retry that one blindly.

## 2. Queue the task

Call `queueTask` — `POST /taskroutingapi/v1/task/` with `Content-Type: application/json`.

Always send `extTaskId`, and send `extCaseId` / `extContactId` when you have them. **These are the
idempotency contract for this API.** Bright Pattern looks for an existing task, case or contact already
linked to each external ID, reuses the record if it finds one and creates it if it does not. Send the same
`extTaskId` twice and you get application error code `5` ("Task is or already was in the queue", HTTP `400`)
instead of a duplicate task — so treat that code as *success, already queued*, not as a failure.

Set `serviceName` to a service of type **Task**; anything else returns code `6`. Optional fields worth
setting: `priority`, `order` (`fifo`), `screenpop` / `screenpopData` to pop the right CRM record on the
agent's desktop, and the `contactInfo` / `caseInfo` / `taskInfo` blocks.

## 3. Track it

- `queryTask` — `GET /taskroutingapi/v1/task/{taskid}/?external=true` returns status and queue position.
  Pass `external=true` when `{taskid}` is your `extTaskId` rather than a Bright Pattern id.
- `updateTask` — `PATCH /taskroutingapi/v1/task/{taskid}` changes attributes such as service or priority
  while the task is still queued.
- `cancelTask` — `DELETE /taskroutingapi/v1/task/{taskid}/` removes it from the queue and sets a
  disposition. Once an agent has taken it you get code `10` and cannot cancel.
- `cancelServiceTasks` — `DELETE /taskroutingapi/v1/service` cancels every queued task for one service.
  This is destructive and unscoped to a single task; confirm with a human before calling it.

## Error handling

Bright Pattern does **not** use RFC 9457 problem details here — it returns a numeric application code
alongside the HTTP status. The full table is in `errors/bright-pattern-problem-types.yml`. Back off on
`429` (code `12`, API limit exceeded) and on `502` (code `11`, no servers available); neither is a
client-side bug.
