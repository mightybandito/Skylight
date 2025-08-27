# Docs Site

Two static viewers are included:
- `docs-site/swagger.html` (Swagger UI)
- `docs-site/redoc.html` (Redoc)

They load the spec from `openapi/openapi.yaml`.

## GitHub Pages

1. Commit & push to `main` (or `master`).
2. In repo settings → Pages, set **Source** to **GitHub Actions**.
3. The included workflow `.github/workflows/pages.yml` will publish the whole repo.
4. Visit:
   - `/docs-site/swagger.html`
   - `/docs-site/redoc.html`

## Local (no build tools)

Open `docs-site/swagger.html` or `docs-site/redoc.html` in a local HTTP server:
```bash
# from repo root
python3 -m http.server 8080
# then browse http://localhost:8080/docs-site/swagger.html
```