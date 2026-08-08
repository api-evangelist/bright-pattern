---
name: Build a customer-facing web or mobile chat against Bright Pattern
description: Check service availability, request a chat session, long-poll the event stream, send events and files, and close the case using the Mobile/Web Messaging API v2.
api: openapi/bright-pattern-mobile-web-messaging-v2-openapi.yml
operations: [checkAvailability, expectedParameters, getChatWidgetConfiguration, requestChat, getActiveChat, getNewChatEvents, sendEvents, uploadFile, getFile, getIceServers, mobileNotificationSubscription, getCaseHistory, closeCase]
generated: '2026-08-08'
method: generated
---

# Build a customer-facing chat against Bright Pattern

The Mobile/Web Messaging API v2 is the **customer-side** API — it backs the iOS and Android SDKs in
`packages/` and any web chat widget you build yourself. Use v2, not v1.

## Base and required parameter

Everything sits under `https://<tenant>.brightpattern.com/clientweb/api/v2/`, and **every call takes a
`tenantUrl` query parameter** in addition to the host. This API is customer-facing and is not
bearer-token authenticated the way the back-office APIs are — the chat session itself is the credential.

## 1. Before offering chat

- `checkAvailability` — `GET /availability` tells you whether the service can take a chat right now.
  Gate your UI on this rather than letting a customer open a session into an empty queue.
- `expectedParameters` — `GET /parameters` returns what the scenario expects you to collect.
- `getChatWidgetConfiguration` — `GET /configuration` returns the widget config.

## 2. Start and drive the session

- `requestChat` — `POST /chats` opens the session and returns a `chatId`.
- `getActiveChat` — `GET /chats/active` resumes an existing session, e.g. after an app restart.
- `getNewChatEvents` — `GET /chats/{chatId}/events` is a **long poll**: with no new events the server
  holds the request open for roughly 5–15 seconds. Issue exactly one at a time — a second request while
  one is still held returns `400`. On `429` back off before re-polling.
- `sendEvents` — `POST /chats/{chatId}/events` sends client-side events (messages, typing, delivered
  and read receipts).
- `getChatHistory` — `GET /chats/{chatId}/history` for the transcript.

## 3. Rich media

- `uploadFile` — `POST /files`, then `getFile` — `GET /chats/{chatId}/files/{fileId}`.
- `getAgentProfilePhoto` — `GET /chats/{chatId}/profilephotos/{partyId}`.
- `getIceServers` — `GET /iceservers` supplies the ICE servers you need before starting a WebRTC voice
  or video leg.

## 4. Mobile and case lifecycle

- `mobileNotificationSubscription` — `POST /chats/{chatId}/notifications` registers an APNs or Firebase
  token so the customer is notified when the app is backgrounded.
- `getCaseHistory` — `GET /casehistory` returns combined transcripts of every chat session linked to the
  CRM case.
- `closeCase` — `POST /closecase` closes the case behind the session.

## Don't hand-roll what is already packaged

For native apps use the first-party SDKs rather than these endpoints directly:
`pod 'BPMobileMessaging'` (iOS) and `com.github.ServicePattern:MobileAPI_Android` (Android). See
`packages/bright-pattern-packages.yml`.
