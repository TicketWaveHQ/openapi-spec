# Contributing to TicketWave OpenAPI spec

Thank you for opening an issue or PR. This repository holds the single canonical OpenAPI 3.1 document for the TicketWave API. Because downstream SDKs and the official documentation viewer are generated from `openapi.yaml`, even small changes can ripple — please follow the rules below.

## Ground rules

- **One source of truth.** `openapi.yaml` is canonical. Do not split it.
- **Semantic versioning.** Bump `info.version` per the rules in [`README.md`](./README.md#versioning-policy):
  - `patch` — documentation, descriptions, examples.
  - `minor` — additive only (new endpoints, optional fields, new enum values).
  - `major` — breaking changes. 30-day advance notice required.
- **Changelog every release.** Add a `[x.y.z] — YYYY-MM-DD` block to [`CHANGELOG.md`](./CHANGELOG.md).
- **Brand canon.** The product is the **TicketWave API** (not "Access API"). URLs use the apex `ticketwavehq.com` — no `www.` prefix.

## Local checks

```bash
npx --yes @redocly/cli@latest lint openapi.yaml
npx --yes @apidevtools/swagger-cli@latest validate openapi.yaml
```

CI runs both on every PR via [`.github/workflows/validate.yml`](./.github/workflows/validate.yml).

## Filing a spec discrepancy

If the live API behaves differently from the spec, open an issue using the **"Spec discrepancy"** template at [`.github/ISSUE_TEMPLATE/spec-discrepancy.yml`](./.github/ISSUE_TEMPLATE/spec-discrepancy.yml). Include the request, the actual response, and the expected response per the spec.

## Pull request expectations

- Title: imperative mood, scoped (e.g. `feat(v2-rules): add ...`, `chore: ...`, `docs: ...`).
- Description: what changed, why, and any version bump rationale.
- One logical change per PR.
- CI must be green.
- Code-owner review per [`CODEOWNERS`](./.github/CODEOWNERS).

## Code of conduct

Participation is governed by [`CODE_OF_CONDUCT.md`](./CODE_OF_CONDUCT.md).

## Security

Do not file security issues here. See [`SECURITY.md`](./SECURITY.md) for the private disclosure channel.
