# Unofficial Skylight API (Community Reference)

> **Purpose**: A community-maintained reference for documenting the network endpoints used by the Skylight apps, based on observed traffic.  
> **Scope**: Reverse-engineered, incomplete, and **unofficial**. Not affiliated with Skylight. For research, interoperability, and educational use only.

---

## Disclaimers

- Respect the app’s Terms of Service and privacy laws. Only capture traffic from your own account/devices.
- Redact personal data and secrets (tokens, emails, IDs tied to real people) before committing.
- This repository **does not** encourage abusing the service or bypassing protections.

## How this repo is organized

- `openapi/openapi.yaml` — A living OpenAPI 3.1 spec for discovered endpoints.
- `examples/` — Example requests/responses (redacted).
- `docs/` — How-to guides (capturing traffic, auth notes, etc.).
- `CONTRIBUTING.md` — How to add endpoints, schemas, and examples safely.
- `SECURITY.md` — Responsible redaction guidelines.
- `LICENSE` — Default: CC BY-NC 4.0 (adjust as you prefer).

## Base URL

```
https://app.ourskylight.com
```

Most endpoints appear to be under `/api/...` and follow a **JSON:API** style structure (`type`, `id`, `attributes`, `relationships`).

## Authentication

Skylight’s mobile app uses a Bearer token. Example header (token redacted):

```
Authorization: Bearer <REDACTED>
```

Tokens typically rotate; treat them as secrets and never commit real values.

## Example Endpoint (documented so far)

- `GET /api/frames/{frameId}/chores` — List chores for a frame (household) within date bounds.

See the OpenAPI spec for parameters and a redacted example response.

## Tools & Workflow

- **Capture**: Charles/Proxyman/mitmproxy (with SSL cert installed).
- **Inspect**: Confirm hostnames and query params; export sanitized samples to `examples/`.
- **Document**: Update `openapi/openapi.yaml` and add any new schemas/components.
- **Test**: Use Postman/Insomnia to verify requests (with your own credentials).

## Roadmap

- Add auth/login flow (if observable).
- Expand coverage: chores create/update, categories, profiles, frames, rewards, schedules.
- Note rate limits, error shapes, and pagination once understood.

---

Maintainers: add yourself to `docs/maintainers.md` if you contribute regularly.


## v0.2.0
- Added Categories, Devices, Lists, Task Box endpoints and schemas.
- Added Basic token auth scheme in addition to Bearer.


## v0.3.0
- Added Frames, Source Calendars, Calendar Events, Rewards, Reward Points paths.
- Expanded `list_item` schema; corrected color fields to accept `#RRGGBB`.
- Ensured `chore.status` captured explicitly.


## Authentication
See [docs/auth.md](docs/auth.md) for guidance on capturing and using your own token.


## Auth tokens
See **docs/auth.md** for how to capture a token safely.


## Interactive Docs
You can explore the API spec in a browser:

# Unofficial Skylight API (Community Reference)

> **Purpose**: A community-maintained reference for documenting the network endpoints used by the Skylight apps, based on observed traffic.  
> **Scope**: Reverse-engineered, incomplete, and **unofficial**. Not affiliated with Skylight. For research, interoperability, and educational use only.

---

## Disclaimers

- Respect the app’s Terms of Service and privacy laws. Only capture traffic from your own account/devices.
- Redact personal data and secrets (tokens, emails, IDs tied to real people) before committing.
- This repository **does not** encourage abusing the service or bypassing protections.

## How this repo is organized

- `openapi/openapi.yaml` — A living OpenAPI 3.1 spec for discovered endpoints.
- `examples/` — Example requests/responses (redacted).
- `docs/` — How-to guides (capturing traffic, auth notes, etc.).
- `CONTRIBUTING.md` — How to add endpoints, schemas, and examples safely.
- `SECURITY.md` — Responsible redaction guidelines.
- `LICENSE` — Default: CC BY-NC 4.0 (adjust as you prefer).

## Base URL

```
https://app.ourskylight.com
```

Most endpoints appear to be under `/api/...` and follow a **JSON:API** style structure (`type`, `id`, `attributes`, `relationships`).

## Authentication

Skylight’s mobile app uses a Bearer token. Example header (token redacted):

```
Authorization: Bearer <REDACTED>
```

Tokens typically rotate; treat them as secrets and never commit real values.

## Example Endpoint (documented so far)

- `GET /api/frames/{frameId}/chores` — List chores for a frame (household) within date bounds.

See the OpenAPI spec for parameters and a redacted example response.

## Tools & Workflow

- **Capture**: Charles/Proxyman/mitmproxy (with SSL cert installed).
- **Inspect**: Confirm hostnames and query params; export sanitized samples to `examples/`.
- **Document**: Update `openapi/openapi.yaml` and add any new schemas/components.
- **Test**: Use Postman/Insomnia to verify requests (with your own credentials).

## Roadmap

- Add auth/login flow (if observable).
- Expand coverage: chores create/update, categories, profiles, frames, rewards, schedules.
- Note rate limits, error shapes, and pagination once understood.

---

Maintainers: add yourself to `docs/maintainers.md` if you contribute regularly.


## v0.2.0
- Added Categories, Devices, Lists, Task Box endpoints and schemas.
- Added Basic token auth scheme in addition to Bearer.


## v0.3.0
- Added Frames, Source Calendars, Calendar Events, Rewards, Reward Points paths.
- Expanded `list_item` schema; corrected color fields to accept `#RRGGBB`.
- Ensured `chore.status` captured explicitly.


## Authentication
See [docs/auth.md](docs/auth.md) for guidance on capturing and using your own token.


## Auth tokens
See **docs/auth.md** for how to capture a token safely.


## Interactive Docs
You can explore the API spec in your browser:

- [Swagger UI](docs/swagger.html) — interactive “try it” interface
- [Redoc](docs/redoc.html) — clean reference-style docs

> On GitHub Pages these will be accessible at:  
> https://`{user}`.github.io/`{repo}`/swagger.html  
> https://`{user}`.github.io/`{repo}`/redoc.html
