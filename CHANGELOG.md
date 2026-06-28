# Changelog

All notable changes to the TicketWave API OpenAPI specification are recorded in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html) per the rules in [`README.md`](./README.md#versioning-policy).

## [1.0.1] — 2026-06-28

Brand-name canon alignment + apex URL sweep. No wire-format changes.

### Changed

- `info.title` renamed from "TicketWave Access API" to "TicketWave API" to align with the canonical brand name (canon §3).
- All `www.ticketwavehq.com` references swept to the apex `ticketwavehq.com`:
  - `info.contact.url`
  - `info.license.url`
  - `info.description` (api-keys URL)
  - `servers[1].url` (dashboard alias)
  - `components.securitySchemes.apiKey.description` (api-keys URL)
  - README License section
  - this CHANGELOG (footer reference below)

[1.0.1]: https://github.com/TicketWaveHQ/openapi-spec/releases/tag/v1.0.1

## [1.0.0] — 2026-06-25

Initial public release of the spec.

### Added

- `openapi.yaml` — OpenAPI 3.1 document for the TicketWave Access API.
- `/api/v1/*` namespace — read tenant resources:
  - Events (`/api/v1/events`, `/api/v1/events/{eventSlug}`)
  - Ticket tiers (`/api/v1/events/{eventSlug}/tiers`)
  - Orders (`/api/v1/orders`, `/api/v1/orders/{orderId}`) — PII gated by `plugin:pii` scope; `CustomerMasked` returned by default.
- `/api/v2/*` namespace — the access-decision engine:
  - Decisions (`/api/v2/decisions`, `/api/v2/decisions/{decisionId}`, `/api/v2/decisions/{decisionId}/replay`)
  - Rules (`/api/v2/rules` CRUD, stage management)
  - Resources (`/api/v2/resources` CRUD)
  - Actors (`/api/v2/actors`, `/api/v2/actors/{actorId}/claims`)
  - Disputes (`/api/v2/disputes`, `/api/v2/disputes/{disputeId}`)
  - Overrides (`/api/v2/overrides`)
  - Subscriptions (`/api/v2/subscriptions` — HMAC signing secret surfaced once on create)
  - Tenants (`/api/v2/tenants/self`)
  - Shadow-mode triage (`/api/v2/shadow/disagreements`)
  - System events feed (`/api/v2/system/events`)
- Bearer-token security scheme (`apiKey`) with `tw_live_*` token format documentation.
- 14 tags grouping the surface by domain.
- 64 component schemas covering requests, responses, and shared envelopes (`OffsetPagination`, `LimitPagination`, `Money`, `CustomerMasked`, `Tenant`, `Decision`, `Rule`, `Resource`, `Actor`, `Dispute`, `Override`, `Subscription`, `SystemEvent`, …).
- Canonical server `https://access.ticketwavehq.com` listed first; dashboard alias `https://ticketwavehq.com` listed second (both resolve to the same deployment).
- Rate-limit guidance: 120 req/min/key on v1, 240 req/min/key on v2.

### Surface counts

| Item | Count |
|---|---|
| Paths | 26 |
| Operations | 37 |
| Component schemas | 64 |
| Tags | 14 |

### Notes

- Webhook signature verification (HMAC-SHA256) is documented out-of-band at <https://access.ticketwavehq.com/help>. The OpenAPI 3.1 `webhooks` block does not yet round-trip HMAC details through every code generator, so we keep that contract human-readable for now.
- Routes marked `# TODO` in the source are passthroughs of underlying rows whose shape is not yet pinned; future minor releases will harden those schemas additively.

[1.0.0]: https://github.com/TicketWaveHQ/openapi-spec/releases/tag/v1.0.0
