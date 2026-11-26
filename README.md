# Japan Driving Check

Free checker for driving in Japan on a foreign license: which document your country needs (1949 Geneva IDP, Japanese translation for Germany/Switzerland/France/Belgium/Monaco/Taiwan, or no route), your exact last driving day (1 year from landing, IDP validity, home-license expiry, the residents' 3-month rule), and whether you can convert to a Japanese license (外免切替) after the 2025-10-01 changes (住民票 required, test exemptions incl. US states, 50-question knowledge check, Tokyo fees, reported pass rates).

- Full app and API (Vercel): https://japan-driving-check.vercel.app
- Checker (GitHub Pages): https://akiba-labs.github.io/japan-driving-check/
- API: `GET /api/check?country=US&usState=CA&document=idp&entryDate=2026-11-01&idpIssueDate=2026-06-15` (keyless, CORS), `/api/rules`, `/openapi.json`, `/llms.txt`
- MCP: `japan_driving_check` on https://free-agent-tools.vercel.app/mcp

Sources: NPA 外国免許をお持ちの方へ; Tokyo Metropolitan Police pages on the Geneva Convention list (NPA data, May 2026), foreign licenses with translation, IDPs, 外免切替 and the 2025-10-01 changes; JAF. Rules as of 2026-10-27.

**Disclaimer:** educational, not legal advice, not affiliated with the National Police Agency, prefectural police or JAF. Driving without a valid license is a crime in Japan; confirm with the police or your rental company.

Dev:

```bash
npm ci
npm test
npm run build
npm run build:pages
```

`npm run build` is the Vercel app (checker, JSON API, share pages). `npm run build:pages` writes a static `out/` for GitHub Pages and checks that internal links and assets resolve under `/japan-driving-check`. Server routes stay in the repo; the Pages script only moves them aside for that build.

GitHub settings: **Settings → Pages → Build and deployment → Source: GitHub Actions**. Pushes to `main` deploy with `.github/workflows/pages.yml`. The copy-paste steps for the other tool repos are at the top of `scripts/build-pages.mjs`.
