# Bright Pattern

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Bright Pattern is a cloud contact center (CCaaS) software company whose omnichannel platform routes voice, IVR, email, chat, SMS/MMS, video and social messenger conversations to agents, with built-in quality management, workforce management, outbound dialing and AI/bot assistance. The platform is multi-tenant: every customer contact center runs on its own tenant hostname, and Bright Pattern exposes nine public REST API families against that tenant — Configuration, SCIM-compliant user provisioning, List Management (v2, v3.0, v3.2), Task Routing, SMS/MMS, Interaction Content (call recordings and metadata), Real-Time Statistics, and the Mobile/Web Messaging APIs (v1 and v2) that back the iOS and Android Mobile SDKs. The public API reference is published as Postman documenter collections linked from the Bright Pattern documentation wiki.

**Areas:** Company · Contact Center · CCaaS · Customer Experience · Omnichannel · Call Center · Telephony · Messaging · SMS · Voice · Customer Service · Workforce Management

## Bright Pattern on APIs.io

Everything profiled for Bright Pattern is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/bright-pattern/](https://apis.io/providers/bright-pattern/)** — or go straight to one of the APIs or properties below.

### APIs (14)

- [Bright Pattern Authentication API](https://apis.io/apis/bright-pattern/bright-pattern-authentication-api/) — The OAuth 2.0 Client Credentials Grant is used to authenticate clients of this API. The authenticated user is checked for having appropriate privileges to…
- [Bright Pattern Calling List API](https://apis.io/apis/bright-pattern/bright-pattern-calling-list-api/) — The Calling List API from Bright Pattern — 8 operation(s) for calling list.
- [Bright Pattern Campaigns API](https://apis.io/apis/bright-pattern/bright-pattern-campaigns-api/) — The Campaigns API from Bright Pattern — 27 operation(s) for campaigns.
- [Bright Pattern DNC Lists API](https://apis.io/apis/bright-pattern/bright-pattern-dnc-lists-api/) — Bright Pattern's List Management API makes it easy to manage the contents of Do Not Call (DNC) lists with bulk delete, add, and replace actions. The API…
- [Bright Pattern Do Not Call List API](https://apis.io/apis/bright-pattern/bright-pattern-do-not-call-list-api/) — The Do Not Call List API from Bright Pattern — 4 operation(s) for do not call list.
- [Bright Pattern Link Groups API](https://apis.io/apis/bright-pattern/bright-pattern-link-groups-api/) — Bright Pattern's List Management API provides the ability to manage Link Groups so several campaigns can be linked together. When processing all records of…
- [Bright Pattern Lists API](https://apis.io/apis/bright-pattern/bright-pattern-lists-api/) — Bright Pattern's List Management API streamlines the creation and deletion of lists and formats and provides a convenient way to manage list records. Note:…
- [Bright Pattern Methods API](https://apis.io/apis/bright-pattern/bright-pattern-methods-api/) — The Methods API from Bright Pattern — 32 operation(s) for methods.
- [Bright Pattern Multichannel Call Recordings API](https://apis.io/apis/bright-pattern/bright-pattern-multichannel-call-recordings-api/) — These methods are used to extract individual segments of multichannel call recordings (i.e., recordings where voice of each paricipating party is recorded…
- [Bright Pattern Phones API](https://apis.io/apis/bright-pattern/bright-pattern-phones-api/) — With the https://:tenant/configapi/v2/phone endpoint you can: Get a list of all contact center users with their extensions and DID numbers Get a list of all…
- [Bright Pattern Regular Call Recordings API](https://apis.io/apis/bright-pattern/bright-pattern-regular-call-recordings-api/) — These methods enable retrieval of regular voice recordings (i.e., recordings where voices of all participating parties are recorded in the same audio file)…
- [Bright Pattern SMS/MMS Messaging API](https://apis.io/apis/bright-pattern/bright-pattern-sms-mms-messaging-api/) — These methods enable sending of SMS and MMS messages and checking the delivery status. The response parameters are explained below. Response parameters…
- [Bright Pattern Task Routing API](https://apis.io/apis/bright-pattern/bright-pattern-task-routing-api/) — The following methods allow tasks within Bright Pattern Contact Center to be queued, canceled, updated, and queried.
- [Bright Pattern Users API](https://apis.io/apis/bright-pattern/bright-pattern-users-api/) — With the https://:tenant_url/configapi/v2/user endpoint you can: Create new users and define most of their attributes Update existing users Check and clear…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [bright-pattern](https://apis.io/servers/bright-pattern/bright-pattern/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Bright Pattern Agentic Access](https://apis.io/agentic-access/bright-pattern/bright-pattern-agentic-access/)

#### Collections (14)

Postman and Open Collection request collections.

- [Bright Pattern Authentication API](https://apis.io/collections/bright-pattern/open-bright-pattern-authentication-api/)
- [BPCC List Management API v2.0 Calling List API](https://apis.io/collections/bright-pattern/open-bright-pattern-calling-list-api/)
- [Bright Pattern Campaigns API](https://apis.io/collections/bright-pattern/open-bright-pattern-campaigns-api/)
- [Bright Pattern DNC Lists API](https://apis.io/collections/bright-pattern/open-bright-pattern-dnc-lists-api/)
- [BPCC List Management API v2.0 Do Not Call List API](https://apis.io/collections/bright-pattern/open-bright-pattern-do-not-call-list-api/)
- [BPCC List Management API v3.2 Link Groups API](https://apis.io/collections/bright-pattern/open-bright-pattern-link-groups-api/)
- [Bright Pattern Lists API](https://apis.io/collections/bright-pattern/open-bright-pattern-lists-api/)
- [Bright Pattern Methods API](https://apis.io/collections/bright-pattern/open-bright-pattern-methods-api/)
- [BPCC Interaction Content Multichannel Call Recordings API](https://apis.io/collections/bright-pattern/open-bright-pattern-multichannel-call-recordings-api/)
- [BPCC Configuration Phones API](https://apis.io/collections/bright-pattern/open-bright-pattern-phones-api/)
- [BPCC Interaction Content Regular Call Recordings API](https://apis.io/collections/bright-pattern/open-bright-pattern-regular-call-recordings-api/)
- [BPCC SMS/MMS SMS/MMS Messaging API](https://apis.io/collections/bright-pattern/open-bright-pattern-sms-mms-messaging-api/)
- [BPCC Task Routing API](https://apis.io/collections/bright-pattern/open-bright-pattern-task-routing-api/)
- [Bright Pattern Users API](https://apis.io/collections/bright-pattern/open-bright-pattern-users-api/)

#### Overlays (11)

OpenAPI overlays, including conversational phrasing for each operation.

- [Bright Pattern Configuration Overlay](https://apis.io/overlays/bright-pattern/bright-pattern-configuration-overlay/)
- [Bright Pattern Interaction Content Overlay](https://apis.io/overlays/bright-pattern/bright-pattern-interaction-content-overlay/)
- [Bright Pattern List Management V2 Overlay](https://apis.io/overlays/bright-pattern/bright-pattern-list-management-v2-overlay/)
- [Bright Pattern List Management V3 2 Overlay](https://apis.io/overlays/bright-pattern/bright-pattern-list-management-v3-2-overlay/)
- [Bright Pattern List Management V3 Overlay](https://apis.io/overlays/bright-pattern/bright-pattern-list-management-v3-overlay/)
- [Bright Pattern Mobile Web Messaging V1 Overlay](https://apis.io/overlays/bright-pattern/bright-pattern-mobile-web-messaging-v1-overlay/)
- [Bright Pattern Mobile Web Messaging V2 Overlay](https://apis.io/overlays/bright-pattern/bright-pattern-mobile-web-messaging-v2-overlay/)
- [Bright Pattern Real Time Statistics Overlay](https://apis.io/overlays/bright-pattern/bright-pattern-real-time-statistics-overlay/)
- [Bright Pattern Scim User Provisioning Overlay](https://apis.io/overlays/bright-pattern/bright-pattern-scim-user-provisioning-overlay/)
- [Bright Pattern Sms Mms Overlay](https://apis.io/overlays/bright-pattern/bright-pattern-sms-mms-overlay/)
- [Bright Pattern Task Routing Overlay](https://apis.io/overlays/bright-pattern/bright-pattern-task-routing-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Bright Pattern Authentication](https://apis.io/security/bright-pattern/bright-pattern-authentication/)
- [Bright Pattern Domain Security](https://apis.io/security/bright-pattern/bright-pattern-domain-security/)
- [Bright Pattern Trust Center](https://apis.io/security/bright-pattern/bright-pattern-trust-center/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.brightpattern.com/)
- [Documentation](https://help.brightpattern.com/)
- [Getting started](https://help.brightpattern.com/latest:Tutorials-for-admins/API/Access)
- [API reference](https://help.brightpattern.com/latest:Api)
- [Pricing](https://www.brightpattern.com/call-center-software-pricing/)
- [Sign up](https://www.brightpattern.com/contact-bright-pattern/)
- [Support](https://www.brightpattern.com/contact-center-support/)
- [Changelog](https://help.brightpattern.com/WhatsNew)
- [Blog](https://www.brightpattern.com/blog/)
- [Compliance](https://www.brightpattern.com/compliance/)
- [Terms of service](https://www.brightpattern.com/terms-conditions/)
- [Privacy policy](https://www.brightpattern.com/privacy-policy/)
- [GitHub](https://github.com/ServicePattern)

## API Evangelist rating

**Kin Score 52.2** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 49.6 |
| Contract governance | 18.2 |
| Operational transparency | 18.4 |
| Developer ergonomics | 70.8 |
| Access clarity | 60.5 |

**Agent readiness 30.4** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | — |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | — |

**Regulatory alignment 25.0** — Telecommunications

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/bright-pattern/](https://apis.io/providers/bright-pattern/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Bright Pattern: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/bright-pattern/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
