---
name: Load a calling list and run an outbound campaign
description: Create a calling list, load records into it, bind it plus a Do Not Call list to a campaign, start and stop the campaign, and read completed records back.
api: openapi/bright-pattern-list-management-v3-2-openapi.yml
operations: [getAccessToken, createList, addManyRecords, bindList, bindDncList, start, getCampaignStatus, stop, getCompletedRecords, getUpdatedRecords]
generated: '2026-08-08'
method: generated
---

# Load a calling list and run an outbound campaign

Use List Management API **v3.2** — v3.0 and v2.0 are still published but v3.2 is current, and v2.0
addresses lists by *name* rather than id.

## 1. Authenticate

`getAccessToken` — `POST /configapi/v3/oauth/token` (note: **v3**, not v2, for this API family).

## 2. Build the list

- `createList` — `POST /configapi/v3/callinglist/createList`, or `createListWithNewFormat` when the
  records need a new field layout.
- `addManyRecords` — `POST /configapi/v3/callinglist/addAll/{list_id}` for bulk load; `addRecord`
  (`.../add/{list_id}`) for one.
- Long-running list operations return a job id. Poll `getJobStatus` —
  `GET /configapi/v3/job/{job_id}` — until it completes. Do **not** assume the write landed when the
  call returns.
- `updateManyRecords`, `updateRecord`, `deleteManyRecords`, `deleteAllRecords` and `eraseRecord` cover
  the rest of the record lifecycle. `eraseRecord` is the compliance-grade removal; prefer it when a
  record must be scrubbed rather than merely deleted.

## 3. Attach the list and the suppression list to a campaign

- `bindList` — `POST /configapi/v3/campaign/bindList/{campaign_id}`
- `bindDncList` — `POST /configapi/v3/campaign/bindDNCList/{campaign_id}`

**Bind the Do Not Call list before you start dialing.** Bright Pattern sells this platform on TCPA
compliance; a campaign started without its DNC list bound is the failure mode that matters here.
`createDncList`, `addManyRecordsDNCLists` and `getDncRecords` manage the DNC side.

## 4. Run it

- `start` — `POST /configapi/v3/campaign/start/{campaign_id}`
- `getCampaignStatus` — `GET /configapi/v3/campaign/getStatus/{campaign_id}`
- `stop` — `POST /configapi/v3/campaign/stop/{campaign_id}`

Starting a campaign already running returns `409 Conflict` ("Campaign is already in the requested
state"). Treat that as a no-op, not an error.

## 5. Read results back

- `getCompletedRecords` — `POST /configapi/v3/campaign/getCompletedRecords/{campaign_id}`
- `getUpdatedRecords` — `POST /configapi/v3/campaign/getUpdatedRecords/{campaign_id}` for the delta
  since your last poll
- `queryARecord` — `POST /configapi/v3/campaign/queryRecord/{campaign_id}` for a single record

Avoid the `.../callinglist/getAll/{list_id}/{campaign_id}`, `.../getChanged/...` and `.../get/...`
operations — they are marked **DEPRECATED** in the published collection; use the campaign-scoped
equivalents above.

## Error handling

This API uses the `{"error": "...", "error_description": "..."}` envelope. Read `error_description` —
Bright Pattern's own documentation says it carries the specific parameter and reason. There is no
idempotency key on any of these writes, so a retried bulk `addAll` after a timeout can double-load a
list. Check with `getList` before retrying.
