---
name: Export call recordings and interaction metadata for compliance
description: Pull regular and multichannel call recording audio plus interaction metadata out of Bright Pattern, and erase recordings with a recorded reason.
api: openapi/bright-pattern-interaction-content-openapi.yml
operations: [getAccessToken, getInteractionMetadata, getRegularRecordingAudioFile, getMultichannelRecordingStructure, getMultichannelRecordingSegmentAudioFile, eraseCallRecordings]
generated: '2026-08-08'
method: generated
---

# Export call recordings and interaction metadata

The Interaction Content API downloads recordings and their metadata — the surface you use for QA
sampling, archival, and for honoring a data-subject erasure request.

## 1. Authenticate

`getAccessToken` — `POST /configapi/v2/oauth/token`. The user the token is issued to must hold the
privilege to access recordings; without it you get `403`, not `404`.

## 2. Identify the interaction

Recordings are keyed by `giid` (global interaction ID, an uppercase UUID) and, within it, `stepid` for
one step of the interaction. Get both from the interaction records search or from a real-time /
reporting source before calling this API — it has no search operation of its own.

## 3. Pull the content

Regular recordings:

- `getInteractionMetadata` — `GET /configapi/v2/recordings/metadata?giid=&stepid=`. Fetch this **first**;
  it tells you whether a recording exists and what it covers.
- `getRegularRecordingAudioFile` — `GET /configapi/v2/recordings/audio?giid=&stepid=` returns the audio.

Multichannel recordings:

- `getMultichannelRecordingStructure` — `GET /configapi/v2/multi_channel_recordings?giid=` returns the
  segment structure.
- `getMultichannelRecordingSegmentAudioFile` —
  `GET /configapi/v2/multi_channel_recordings/audio?giid=&iid=&party=&recid=` pulls one segment. Walk
  the structure to get the `iid`, `party` and `recid` values; do not guess them.

## 4. Erase

`eraseCallRecordings` — `DELETE /configapi/v2/recordings/audio?giid=&reason=` deletes recordings and
records **why**. This is irreversible and there is no idempotency key, so:

- Confirm with a human before calling it.
- Always populate `reason` — it is the audit trail for a HIPAA, GDPR or PCI erasure.
- Verify with `getInteractionMetadata` afterwards rather than assuming the delete landed.

## Handling and errors

Audio responses are binary; do not try to parse them as JSON. `404` on a `GET` means the interaction or
audio file does not exist for that `giid`/`stepid` pair. `415` means you sent no `Content-Type` or the
wrong one. Full table in `errors/bright-pattern-problem-types.yml`.
