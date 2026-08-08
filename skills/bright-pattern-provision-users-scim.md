---
name: Provision Bright Pattern users over SCIM 2.0
description: Create, read, update, replace and delete contact-center users through the SCIM-compliant provisioning endpoint, and fall back to the Configuration API for team and lock-state operations.
api: openapi/bright-pattern-scim-user-provisioning-openapi.yml
operations: [getAccessToken, createUser, getUserById, getUserByUsername, replaceUserProperties, updateUser, deleteUser]
generated: '2026-08-08'
method: generated
---

# Provision Bright Pattern users over SCIM 2.0

Bright Pattern exposes a SCIM 2.0 endpoint so an identity provider can keep contact-center users in sync.

## 1. Authenticate

`getAccessToken` — `POST /configapi/v2/oauth/token`, client-credentials grant. Send the result as
`Authorization: Bearer <access_token>`.

## 2. Work the user lifecycle

| Intent | Operation | Call |
|---|---|---|
| Create | `createUser` | `POST /configapi/v2/scim/users` |
| Read by id | `getUserById` | `GET /configapi/v2/scim/users/{id}` |
| Look up by username | `getUserByUsername` | `GET /configapi/v2/scim/users?filter=userName eq "jane.doe"` |
| Replace every attribute | `replaceUserProperties` | `PUT /configapi/v2/scim/users/{id}` |
| Change only some attributes | `updateUser` | `PATCH /configapi/v2/scim/users/{id}` |
| Deprovision | `deleteUser` | `DELETE /configapi/v2/scim/users/{id}` |

Use `PATCH` (`updateUser`) for partial change. `PUT` (`replaceUserProperties`) replaces **all** existing
attributes with the set you send — anything you omit is dropped, which is the usual way an IdP sync
silently wipes a user's team or role.

`getUserByUsername` is the only list-style read, and it is filter-only: there is no pagination on this
API, so do not attempt to enumerate all users.

## 3. What SCIM does not cover

The SCIM endpoint handles users. For the rest, drop to the Configuration API
(`openapi/bright-pattern-configuration-openapi.yml`):

- `getTeams` — `GET /configapi/v2/team`
- `getUserLockState` / `clearUserLockState` — `GET|PUT /configapi/v2/user/lock/{username}` to read and
  clear a lockout after failed sign-ins
- `getDirectory` / `getAccessNumbers` — `GET /configapi/v2/phone/user`, `GET /configapi/v2/phone/ext`

## Error handling

`409 Conflict` means a user with that unique value (usually `username`) already exists — treat it as
"already provisioned" and reconcile rather than retrying. `404` on a create or update usually means a
*referenced* object is missing (the error body names the type, e.g. "user team not found"), not the user
itself. There is no idempotency key on this API: a retried `POST` after a timeout can create a second
user, so look the username up with `getUserByUsername` before retrying.
