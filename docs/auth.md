# Authentication Guide (How to Capture Your Token)

> **Unofficial reference** — Use only with accounts you own or are authorized to use. Never commit real tokens.

Skylight requests observed so far use either:
- `Authorization: Basic <opaque token>` — **Not** username:password; an opaque bearer-like token.
- `Authorization: Bearer <jwt>` — Standard bearer token (likely JWT).

This guide shows how to capture a token safely for testing documented endpoints.

---

## 1) Capture via Proxy (Recommended)

Use one of these HTTPS debugging proxies:
- **Proxyman** (macOS GUI)
- **Charles Proxy** (macOS/Windows GUI)
- **mitmproxy** (CLI; scriptable)

### Steps
1. **Install and trust** the proxy's root certificate (System Keychain).
2. Enable **SSL Proxying** / **HTTPS capture**.
3. Launch the Skylight app and **log in**.
4. In the proxy session list, find the first authenticated request (e.g., `GET /api/frames/{frameId}/chores`).
5. Copy the **Authorization** header value.

> Tip: If you only see `CONNECT` entries or 4xx errors, enable SSL for the specific hostname and try again.

### Safety
- Tokens are secrets. **Do not** commit real values.
- When sharing examples, replace with `REDACTED` and keep the structure (header name/value format).

---

## 2) Electron/Chromium Apps (DevTools)

If the desktop app is Electron/Chromium-based:

1. Try **View → Toggle Developer Tools** from the app menu, or launch with:
   ```bash
   open -na "/Applications/Skylight.app" --args --remote-debugging-port=9222
   ```
2. Open Chrome → `chrome://inspect` → **inspect** the Skylight target.
3. Go to **Network** tab → click an API call → **Headers** → copy `Authorization`.

This avoids TLS interception and certificate pinning issues.

---

## 3) If HTTPS Decryption Fails (Certificate Pinning)

Some apps validate the server certificate in code (“pinning”). If your proxy shows CONNECT tunnels but no decrypted traffic:

- Try a different proxy (Proxyman/Charles/mitmproxy).
- Use **Frida** to hook common pinning points (`SecTrustEvaluate`, `NSURLSession`, Alamofire) on macOS.
- Run Skylight in a **VM** or use **transparent proxying** (e.g., mitmproxy as gateway) to redirect traffic.

> **Note**: Respect the app’s ToS and local laws. Use these techniques only for legitimate interoperability/debugging.

---

## 4) Using the Token (Postman/Insomnia/cURL)

- Add the header to your request:
  ```http
  Authorization: Basic REDACTED
  ```
  **or**
  ```http
  Authorization: Bearer REDACTED
  ```

- Example cURL:
  ```bash
  curl 'https://app.ourskylight.com/api/frames/REDACTED/chores?after=2025-08-25&before=2025-08-29'     -H 'Authorization: Basic REDACTED'     -H 'Accept: application/json'
  ```

If you receive **401 Unauthorized**:
- Log out/in in the Skylight app and recapture a fresh token.
- Ensure you copied the header **exactly** (no whitespace changes).

---

## 5) Redaction & Sharing

When contributing examples to this repo:
- Replace tokens and any PII with `REDACTED` (keep keys/shape intact).
- Use stable placeholders for related IDs if structure matters (e.g., `"CATEGORY_REDACTED"`).

See also: `../SECURITY.md` and `../CONTRIBUTING.md`.