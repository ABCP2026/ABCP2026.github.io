# ABCP Portal entry point

This public repository contains only a minimal static browser redirect for `https://apps.corrosion.co.il`.

It contains no employee data, credentials, portal source code, Google Sheet identifiers, or runtime authorization logic. The destination is the approved ABCP Portal PROD Apps Script web app:

`https://script.google.com/a/macros/corrosion.co.il/s/AKfycbx985HH_f2GamkAmGRz39HTAMP6dt8SWSMukcipV_CIClKK1S1swodw9IaEjKtbkrWw/exec`

The redirect uses `location.replace()` with a Meta Refresh fallback. It is not URL masking, an iframe, or a reverse proxy; the browser leaves the GitHub Pages origin before the Portal loads, so Google Workspace authentication continues at the supported Apps Script host.

## DNS handoff

The GitHub Pages custom domain is configured as `apps.corrosion.co.il`. The only DNS change required is:

| Type | Host | Value | TTL |
| --- | --- | --- | --- |
| CNAME | `apps` | `ABCP2026.github.io` | Default / 1 hour |

Do not add a wildcard record, do not alter `www`, and do not change MX records. After DNS propagation, GitHub Pages will provision HTTPS; then enable **Enforce HTTPS** in the Pages settings if it has not enabled automatically.

## Rollback

Remove the single `apps` CNAME record in Wix. The direct Portal PROD URL remains available.
