# Teriyaki Gaming docs — context for Claude

Mintlify docs site for Teriyaki Gaming (deployment subdomain `teriyaki-gaming`;
pushing to main auto-deploys to https://teriyaki-gaming.mintlify.app).

The full project picture — architecture, go-live checklist, design rules —
lives in the companion site repo: `tyguymedia/teriyakigaming-site` (private),
see its `CLAUDE.md` and `DESIGN.md`. This repo must stay visually and verbally
consistent with that design contract (green as accent, plain dev-to-dev voice,
no Japanese script, no hype words).

Structure: `docs.json` (theme/nav — every page must be listed here; two tabs:
"Overview" for site-wide pages, "Inkwell" for the plugin), `index.mdx`
(landing), `buying-and-licensing.mdx`, `asset-packs/overview.mdx`, and
`plugins/inkwell/*` — the full 19-page Inkwell docs (get started, authoring/,
components/, guides/, reference/), imported 2026-08-20 from the Inkwell repo's
`Docs/mintlify/` folder, which remains the authoring source; its root-relative
links get prefixed with `/plugins/inkwell` on import. No screenshots yet —
candidates listed in that folder's HANDOFF.md.

Gotcha: `mint broken-links` false-positives on Windows for pages nested 2+
directories deep (e.g. `plugins/inkwell/*`).
