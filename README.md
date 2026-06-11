# Luminovo Slides

A Claude Code skill that builds Luminovo customer decks in one house style and hosts them on a private Luminovo Slides link.

## What it does

- One locked visual style: Inter, the Luminovo palette, and a dark / light / tint slide system. No style picker and no template library.
- Reads a context file to decide what to show for a given customer situation (audience, proof story, which modules, when to add security or integrations, which slide answers an objection).
- Publishes to a private link through the Luminovo Slides connector. The link works on any device.

## Files

| File | Role |
|---|---|
| `SKILL.md` | The process the skill follows, from inputs to a published link. |
| `luminovo-house-style.html` | The locked house style. Copy its `<style>` block and controller `<script>` into every deck. |
| `luminovo-context.md` | What to show for a given situation: audience, proof bank, integrations, security, and the objection and interest routing. |
| `luminovo-product-slides.html` | Ready product and add-on slides, with a DE / EN toggle. |
| `scripts/extract-pptx.py` | Pull content out of a PowerPoint file. |
| `scripts/export-pdf.sh` | Export a deck to PDF. |

## How to use it

Open the skill in Claude Code and ask for a deck. You can start from a meeting transcript, rough notes, a brain dump, or just a topic and an audience. The skill collects a few inputs (customer name, logo, modules in the offer, AE details), builds the deck in the house style, and publishes a link.

Internal product structure (which add-on goes with which product, what is included where, what is not shipped yet) is used only to decide which slides to show. It never appears on a slide.

## Hosting

Decks are published through the Luminovo Slides connector at `https://slides.luminovo.com/mcp`: publish, update, list, view analytics, and delete. Each page gets a private, unguessable URL and expires 180 days after the last update.

## Language

Decks use simple, professional language. No double dashes and no buzzwords. German decks follow the declension and product naming rules in `SKILL.md`.

## Credit

Based on [frontend-slides](https://github.com/zarazhangrui/frontend-slides) by Zara Zhang (MIT License). The Luminovo house-style version is maintained by Max Hungenbach.
