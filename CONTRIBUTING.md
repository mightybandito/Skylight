# Contributing

Thanks for helping document this unofficial API!

## What to add

- New endpoints (paths, params, request/response shapes).
- Schemas (resources, relationships, enums).
- Redacted examples under `examples/`.

## How to capture & redact safely

1. Use a proxy (Charles/Proxyman/mitmproxy) or DevTools if the app is Electron.
2. Export a request+response pair (curl, HAR, or JSON) and place in `examples/`.
3. **Redact**:
   - Access tokens (Authorization headers), cookies, IDs tied to real people.
   - Emails, phone numbers, addresses, GPS coordinates.
   - Anything you wouldn’t want public.
4. Confirm the example still illustrates structure after redaction.

## Editing the spec

- Edit `openapi/openapi.yaml`. Keep responses aligned with JSON:API where applicable.
- Prefer small, focused PRs (one endpoint at a time).
- Include a short description of how you discovered the endpoint.

## Style

- Use OpenAPI 3.1.
- Put enums on query/path params if observed.
- Keep descriptions objective (“observed behavior”).

## Testing

- Load the spec in Postman/Insomnia/Stoplight to ensure it parses.
- Optional: generate a mocked server to sanity-check examples.

## Legal & Ethics

- Only capture from accounts you own/are authorized to use.
- Don’t automate abusive traffic.
- Respect takedown requests from rights holders.
