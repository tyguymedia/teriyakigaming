# Teriyaki Gaming docs — context for Claude

Mintlify docs site for Teriyaki Gaming (deployment subdomain `teriyaki-gaming`;
pushing to main auto-deploys to https://teriyaki-gaming.mintlify.app).

The full project picture — architecture, go-live checklist, design rules —
lives in the companion site repo: `tyguymedia/teriyakigaming-site` (private),
see its `CLAUDE.md` and `DESIGN.md`. This repo must stay visually and verbally
consistent with that design contract (green as accent, plain dev-to-dev voice,
no Japanese script, no hype words).

Structure: `docs.json` (theme/nav — every page must be listed here),
`index.mdx` (landing), `buying-and-licensing.mdx`, `plugins/inkwell/*`
(scaffold for the in-development Inkwell plugin — `TODO(user)` markers await
real content), `asset-packs/overview.mdx`.

Gotcha: `mint broken-links` false-positives on Windows for pages nested 2+
directories deep (e.g. `plugins/inkwell/*`).
