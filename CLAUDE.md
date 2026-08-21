# Teriyaki Gaming docs — context for Claude

Mintlify docs site for Teriyaki Gaming (deployment subdomain `teriyaki-gaming`).

**Deploy is currently broken and it is not a content problem.** teriyaki-gaming.mintlify.app
returns 404 on every path, pushes produce no check runs, and the repo has no webhooks — the
Mintlify GitHub app is not connected to this repo. Until the owner connects it in
dashboard.mintlify.com (git source `tyguymedia/teriyakigaming`, deploy branch `main`),
pushing here deploys nothing. Verify locally with `npx mint dev` instead.

The full project picture — architecture, go-live checklist, design rules — lives in the
companion site repo: `tyguymedia/teriyakigaming-site` (private), see its `CLAUDE.md` and
`DESIGN.md`. This repo must stay visually and verbally consistent with that design contract
(green as accent, plain dev-to-dev voice, no Japanese script, no hype words).

## Structure

- `docs.json` — theme/nav. Two tabs: **Overview** (site-wide pages) and **Inkwell** (the
  plugin). Every page must be listed here; nothing may be listed that is not a file.
- `index.mdx`, `buying-and-licensing.mdx`, `asset-packs/overview.mdx` — site-wide pages.
- `plugins/inkwell/**` — the 22-page Inkwell documentation.
- `images/inkwell/` — the 17 Inkwell screenshots.

## The Inkwell docs are imported, not authored here

Source of truth is `C:\dev\Inkwell\Docs\mintlify` in the **Inkwell plugin repo**, whose
`HANDOFF.md` states the binding conventions (unique per-page icons, every page ends with
`## Next` + `<CardGroup>`, card icons match the destination's frontmatter icon, terminology,
the facts that must read identically on every page, and the deprecated APIs that must never
be documented). Read that file before touching Inkwell content — and prefer fixing the
source and re-importing over editing here, or the next import silently reverts your edit.

Two transformations are applied on import, because that folder is written for a standalone
site and this is a multi-product one:

1. **Nesting** — pages move to `plugins/inkwell/`, so root-relative cross-links get prefixed:
   `](/authoring/x)` → `](/plugins/inkwell/authoring/x)`, same for `href="/…"`. The prefixed
   roots are exactly: authoring, components, guides, reference, introduction, quickstart,
   installation.
2. **Image namespacing** — `images/` → `images/inkwell/`, and `src="/images/foo.png"` →
   `src="/images/inkwell/foo.png"`. HANDOFF.md asks for the images at the docs root; we
   deviate deliberately so a future asset-pack screenshot cannot collide with an Inkwell one.

Screenshots are **generated, not hand-taken** — `Tools/DocShots/shoot_all.ps1` in the Inkwell
repo drives the editor and positions the numbered callouts from real widget geometry. After a
UI change, re-run it; never re-shoot by hand.

## Open issue for the owner

`installation.mdx` and `reference/faq.mdx` state **UE 5.7**, matching the demo `.uproject`
and build artifacts. The Inkwell repo's `README.md` says "5.4 – 5.7" and `Inkwell.uplugin`
declares no `EngineVersion`. Nothing corroborates the 5.4 end. Reconcile README, `.uplugin`
and the Fab listing by hand, then make the docs match — telling a 5.4 buyer they are
supported is a refund.

## Gotcha

`mint broken-links` false-positives on Windows for pages nested 2+ directories deep
(e.g. `plugins/inkwell/authoring/*`). Verify with `npx mint dev` and real HTTP requests.
