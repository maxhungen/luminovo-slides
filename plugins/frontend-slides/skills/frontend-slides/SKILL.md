---
name: luminovo-slides
description: Create Luminovo sales decks in the single Luminovo house style and host them on Luminovo Slides (https://slides.luminovo.com/mcp). Use when someone wants to build a customer pitch/offer deck, turn a transcript or call notes into slides, or convert a PPT into a Luminovo deck. There is ONE locked visual style — no style picker, no template library.
---

# Luminovo Slides

Create Luminovo customer decks in **one locked house style** and publish them to a private **Luminovo Slides** link via the connector (`https://slides.luminovo.com/mcp`). The reference implementation is **[luminovo-house-style.html](luminovo-house-style.html)** — every deck copies its `<style>` block and controller `<script>` verbatim, then fills in real content and slides.

## Core principles

1. **One house style, locked.** Inter + the Luminovo palette + the dark/light/tint slide system. Never offer a style picker, mood selection, or alternate templates. Do not invent new colors or fonts.
2. **Self-contained HTML.** One file, all CSS/JS inline, external resources only via `https://` CDN (Google Fonts only). This is also exactly what the host requires.
3. **Hosted by default.** The deliverable is a Luminovo Slides URL, not a loose file.
4. **Show the value visually.** Money slides use bars/waterfall/before-after, never raw number boxes.
5. **Fit the viewport.** Each `.slide` is one screen (`100vh`); content uses `clamp()`; never scroll inside a slide. Too much content → split into more slides.
6. **Read the context first.** Before choosing slides, read [luminovo-context.md](luminovo-context.md). It tells you which product leads (EMS vs OEM), which proof to use, which slide answers each objection, and when to add security or integrations. Pull ready module slides from [luminovo-product-slides.html](luminovo-product-slides.html).
7. **Keep internal structure off the slides.** Which add-on belongs to which product, what is included where, and what is not shipped yet are routing context only. They never appear on a slide.

---

## The Luminovo house style (copy, don't reinvent)

Open [luminovo-house-style.html](luminovo-house-style.html) and copy its **entire `<style>` block and the controller `<script>`** into every new deck. That gives you the tokens, the three slide surfaces, reveals, nav dots, progress bar, keyboard nav, and the responsive height guards.

**Tokens** (already in the style block): `--navy #11152F`, `--blue #5767EC`, `--indigo #3D48A5`, `--orange #F59756`, greys `#FCFCFE/#F3F4F6/#858CA0/#434650`, semantics `--green #32D583 / --yellow #FDB023 / --red #F97066`, font **Inter** (300–800).

**The three slide surfaces** — alternate them for rhythm:

| Surface | Class | Use for |
|---|---|---|
| **Dark** (navy→indigo gradient) | `slide dark` | Cover, section dividers, business case / ROI, closing |
| **Light** (`--grey-50`) | `slide light` | Most content, feature grids, agenda |
| **Tint** (`--blue-50`) | `slide tint` | Soft sections, challenges, comparison |

**Slide skeleton** (every slide):
```html
<section class="slide light">
  <div class="brandbar">…luminovo | [Customer]…</div>
  <div class="slide-content">
    <div class="shead"><div class="kicker reveal">Eyebrow</div><h2 class="reveal">Title</h2></div>
    … content, each block with class="reveal" …
  </div>
  <div class="page-num">03 / 07</div>
</section>
```

**Component classes available** (in the style block): `.kicker`, `.lead`, `.mega`, `.badges/.badge`, `.feature-grid/.fcard`, `.checks/.it` (agenda/lists), `.cmp` (comparison table), `.bars/.bar-line/.track/.fill` (value-lever / ROI bars), `.roi-card`, `.ae` (closing contact), `.rings` (cover motif). Add `class="reveal"` to anything that should animate in; add `center` to `.slide-content` to center.

---

## Phase 0: Detect mode

- **New deck** → Phase 1.
- **PPT conversion** → `python scripts/extract-pptx.py <in.pptx> <out>`, confirm extracted content, then Phase 1.5 → Phase 2.
- **Enhance a hosted deck** → fetch it with `get_slide_page`, edit the HTML, push back with `update_slide_page` (same URL). Never create a second page for the same deal.

## Phase 1: Content

Get the raw material: a transcript, call notes, a brain-dump, or bullet points. If they have nothing, ask for the topic + audience. Keep this light — the structure comes from Phase 1.5 + the deck skeleton below.

## Phase 1.2: Decide what to show (read the context)

Read [luminovo-context.md](luminovo-context.md) and let it shape the deck:

- **Audience sets the lead.** EMS leads with Quoting Intelligence, OEM leads with Procurement Intelligence. This drives the lead product, the pains on the challenge slide, and which proof number to open with.
- **Match one proof story** to the customer from the proof bank. Match segment first (EMS vs OEM), then topic (speed, cost, supplier, prototyping, risk). One story per proof slide, lead with the result.
- **Pull only the relevant module slides** from [luminovo-product-slides.html](luminovo-product-slides.html). Show the modules that fit this customer, not the whole catalog.
- **Add security or integrations slides only when the situation calls for it** (regulated buyer, IT or security in the room, a security questionnaire, or a direct question about systems). Use the security and integration facts in the context file.
- **Keep the objection table in mind.** When an objection is likely, include the slide that answers it.
- **Do not put internal product structure on a slide.** The add-on to product mapping, "included in", and "coming soon" status are for your routing decision only.

## Phase 1.5: Pre-generation inputs (collect in ONE grouped message)

> "Before I build the deck, I need a few inputs — some are files (logo, headshot), some are text. Upload files right here in chat and type the rest. I'll wait."

| Input | Collect | If missing |
|---|---|---|
| Customer company name | text | block until provided/skipped |
| Customer logo | upload (SVG/PNG) | don't block — `[CUSTOMER LOGO — REPLACE]` on cover + checklist |
| Modules in offer | Procurement Intelligence / Risk / Both | block |
| Est. annual BOM spend (€) | number | block |
| Minimum contract term | text | block |
| AE name | text | block |
| AE email + LinkedIn | text | block |
| AE headshot | upload (JPG/PNG) | don't block — `[AE HEADSHOT — REPLACE]` on closing + checklist |

Inline the logo and headshot as **base64 data-URIs** so the published page stays self-contained. (Large assets that can't be inlined → `add_slide_asset` after publishing.)

## Copy & content rules

- **Plain language:** simple and professional, short sentences. No double dashes (use a period, comma, colon, or parentheses). No buzzwords (avoid "seamless", "game changer", "leverage", "cutting edge", "best in class"). Prove claims with numbers and named customers, not adjectives.
- **German copy:** verify adjective declension; frame consequences as unrealised opportunity ("ungenutztes Einsparpotenzial", not "hohe Kosten") unless a real cost is documented; avoid procurement jargon buyers won't know ("Einstandspreise", "Bedarfsaggregation"); prefer business-impact words (cost, delay, risk) over operational ones.
- **Product naming:** never "Luminovo Core"/"Core Platform"; present Procurement Intelligence + Risk sold together as one integrated platform; use "Risiko-Dashboard"; never present an unshipped feature as current.
- **Required slides:** cover shows **customer logo + Luminovo logo** and module badges; the challenge slide title includes the **customer name** ("Aktuelle Herausforderungen bei [Customer]"); a **savings table with two scenarios — conservative 5% and target 15%** vs. the BOM spend, with **Year 1 = 2 × Year 2** (so 5%/2.5% and 15%/7.5%, both years shown); **ROI shown visually** (`.bars`); closing slide has the AE photo + name + contact (`.ae`).
- Contract terms (term, notice) are visually subordinate — plain text, not a filled badge.

## Phase 2: Generate

Build the deck as a single self-contained HTML file: copy the house-style `<style>` + controller `<script>`, then author the slides. A typical Luminovo deck:

1. **Cover** (`dark`) — brandbar, kicker, `Luminovo für <span class="accent">[Customer]</span>`, lead, module badges, `.rings`.
2. **Agenda** (`light`) — `.checks.agenda`.
3. **Challenge** (`tint`) — "Aktuelle Herausforderungen bei [Customer]", `.feature-grid` of pains.
4. **Platform / modules** (`light`) — `.feature-grid`; one detail slide per module if needed.
5. **Comparison** (`tint`) — `.cmp` (Luminovo vs. data-service / status quo).
6. **Business case** (`dark`) — `.bars` value levers + `.roi-card`; the savings-scenario table.
7. **Closing** (`dark center`) — CTA + `.ae` contact card.

Verify in a browser screenshot at 1280×720 that nothing overflows and surfaces alternate cleanly. (Optional: keep a DE/EN toggle — see the reference deck — only if the customer wants both languages.)

## Phase 3: Host & share

Ask: _"Publish to a private Luminovo Slides link, export a PDF, or both?"_

**Publish (primary):**
1. Confirm the HTML is self-contained and all `[… — REPLACE]` placeholders are resolved (or the user is OK publishing a draft).
2. `publish_slide_page` with `customer_slug` (e.g. `muster-2026`) + the full `html` → returns a private, unguessable URL.
3. Tell the user: works on any device; unguessable but not access-controlled (share only with intended people); auto-expires 180 days after the last update.
- Update later with `update_slide_page` (same URL). Find/manage decks with `list_slide_pages`, `get_slide_page`, `get_slide_page_analytics`, `delete_slide_page`. Extra files via `add_slide_asset`.

**PDF (secondary):** `bash scripts/export-pdf.sh <html> [out.pdf]` (add `--compact` if >10MB).

**Pre-share checklist** — always print:
```
Before sharing this deck, verify:
[ ] Customer logo — [inserted / PLACEHOLDER]
[ ] AE headshot + contact — [inserted / PLACEHOLDER]
[ ] Savings table — based on €[X] BOM spend · confirm with AE
[ ] All feature claims verified as shipped
[ ] Published link — [URL] (share only with intended recipients)
```
Flag any unverified feature claim: "⚠️ confirm with PM before sharing: [claim]".

---

## Supporting files

| File | Purpose |
|---|---|
| [luminovo-house-style.html](luminovo-house-style.html) | The locked house style — copy its `<style>` + `<script>` into every deck |
| [luminovo-context.md](luminovo-context.md) | What to show for a given situation: audience, proof bank, integrations, security, objection and interest routing. Read in Phase 1.2 |
| [luminovo-product-slides.html](luminovo-product-slides.html) | Ready product and add-on slides (DE/EN). Pull the relevant ones |
| Luminovo Slides connector (`https://slides.luminovo.com/mcp`) | Publish / update / list / asset / analytics / delete |
| [scripts/extract-pptx.py](scripts/extract-pptx.py) | PPT → content extraction |
| [scripts/export-pdf.sh](scripts/export-pdf.sh) | Export a deck to PDF |

> There is no style library and no `STYLE_PRESETS.md` — the house style is the only style. (The old 34-template `bold-template-pack` and Vercel `deploy.sh` are not used.)
