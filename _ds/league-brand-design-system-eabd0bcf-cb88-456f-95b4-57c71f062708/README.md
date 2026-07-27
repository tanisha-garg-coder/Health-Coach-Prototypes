# League Design System

A draft brand + product design system for **League** — the healthcare consumer experience (CX) platform. Use it to mock up League-branded interfaces, decks, prototypes, and marketing artifacts that feel native to the brand.

> ⚠️ **Draft, built from brand primitives.** This system was reverse-engineered from the League logo set, brand typography (Inter Tight), and public-facing product copy on league.com. It was **not** derived from an internal Figma library or product codebase. Treat it as a faithful sketch — some values (spacing scale, semantic color families, full component variants) are our best-informed guess and should be verified against the canonical League brand guidelines when those become available.

---

## About League

Founded in 2014 in Toronto, League is an AI-first healthcare consumer-experience (CX) platform. Payers, providers, employers, and consumer-health brands build on the League platform — now centered on **League AI™**, **League Agent Teams™**, and the patent-pending **Health Story™** — to deliver personalized, omnichannel healthcare experiences to tens of millions of members.

**Tagline / positioning:** "Healthcare's most powerful CX platform."
**Core products referenced in this system:**
- **League AI** — predictive intelligence + multi-agent orchestration
- **Agent Teams** — 24/7 multi-agent care guidance (voice, text, app)
- **Health Story** — unified, plain-language health narrative per member
- **Platform / Health OS** — the underlying PaaS that customers build on

## Sources consulted

This system is grounded in the following materials. None are included in the project — if you have access, refer back to the canonical sources:

- `uploads/` — **League logo set** (glyph, horizontal, vertical in full-colour and white; PNG + SVG) and the complete **Inter Tight** typeface family (18 TTF weights/styles).
- **league.com** — product, messaging, tone-of-voice reference (reviewed Apr 2026).
- **Public press/product releases** — Fall 2025 launch announcements, Series C announcements (for positioning and feature vocabulary).

No Figma file or codebase was provided; if you have access to `@league/brand-kit`, Figma libraries, or the Health OS UI code, please attach them and we will re-run to get pixel-level accuracy on components.

---

## Index — what's in this project

```
README.md                    ← you are here
SKILL.md                     ← Claude Code / Agent Skill manifest
colors_and_type.css          ← source-of-truth: fonts, color vars, semantic tokens, base styles
fonts/                       ← Inter Tight (all 18 weights/styles, TTF)
assets/                      ← logos (glyph / horizontal / vertical × full-colour / white × SVG/PNG)
preview/                     ← Design-System-tab cards (one HTML per concept)
ui_kits/                     ← product UI recreations (see per-kit README)
```

Open `preview/*.html` cards directly, or view the whole system in the project's **Design System** tab.

---

## CONTENT FUNDAMENTALS

League's voice is **confident, clinical-grade, and warm** — the voice of enterprise healthcare software that takes itself seriously but believes in people. It sits between "McKinsey deck" and "modern SaaS product."

### Tone ladder
| Axis | League leans … |
|---|---|
| Formal ↔ Casual | **Formal-leaning**, but plainspoken. No slang, no "hey there!" |
| Emotional ↔ Rational | **Rational first**, with human stakes underneath |
| Serious ↔ Playful | **Serious**, but not grave — energetic |
| Expert ↔ Approachable | **Expert**, translated for decision-makers |

### Writing rules
- **Person: "we" for the company, "you" for the reader/customer.** The end-user is usually "members," "consumers," or "patients" — never "users."
- **No emoji in product or enterprise marketing copy.** (Emoji appears only in social-channel posts, not on the product surface.) This system is emoji-free by default.
- **Sentence case** for headlines, buttons, and navigation. Title Case only for formal product names (League AI, Health Story, Agent Teams).
- **Claim, then quantify.** Messaging consistently pairs a bold statement with a number: "Launch in as little as 6 months," "63 million contracted users," "100 million AI-powered recommendations."
- **Action verbs up front.** "Motivate behaviour change." "Close care gaps." "Digitize, integrate, personalize."
- **Proper-noun product vocabulary** is trademarked and Title Case: **League AI™**, **Agent Teams™**, **Health Story™**, **Health OS™**, **Hueman™**.
- **No idiom, no pop-culture references.** Healthcare sits next to regulators and hospital CIOs.
- **Canadian/US English mix** — League is Toronto-HQ'd. Prefer US spellings (digitize, personalize) for parity with their site.

### Example copy

> **Headline:** Healthcare's most powerful CX platform.
> **Subhead:** League AI combines predictive intelligence, omnichannel engagement, clinical-grade language models, and multi-agent orchestration into one unified platform.
> **CTA:** Explore the platform · Request a demo · See it in action

> **Product-surface microcopy (member-facing):** "Your next step is a quick check-in." · "You're covered for this visit." · "We've saved your progress."

### Things to avoid
- "Revolutionary," "game-changing," "disruption" — dated and over-claimed.
- Emoji on surfaces League actually ships (slides, product UI, deck decks, marketing site).
- Clinical jargon untranslated ("polypharmacy," "SDOH") without a plain-language gloss.
- First-person singular ("I can help you…") — agents speak as League, not as a named persona.

---

## VISUAL FOUNDATIONS

League's visual system is **tight, geometric, and purposeful.** The logo itself is built from three hard-edged squares forming an "L" and a plus — that grid-and-square motif propagates through the whole system.

### Color
- **Three anchor colors** carry the brand: `#501CD2` Blurple Mid (primary/CTAs), `#19063A` Blurple Deepest (dark surfaces), `#F9F7F6` Creme (default light bg). See `colors_and_type.css`.
- **Blurple Mid** is the workhorse — CTAs, key strokes, data highlights, links. Never use it as a page background.
- **Blurple Deep / Blurple Deepest** are the primary text + dark-surface colors. Pure black is avoided.
- Backgrounds are predominantly **Creme (`#F9F7F6`) or white**. Dark surfaces use Blurple Deepest, not black.
- **⛔ Never use Teal (`#00C29B`) in designs.** Teal exists only inside the League logo glyph. Do not use it for success states, accents, icon backgrounds, data viz, eyebrows, stats, decoration, or any UI surface. For positive / "go" beats use the semantic Success green (`--success`, `#2F8F5E`). For accents use Blurple Mid, Lilac, or Periwinkle.
- **Never gradients as a primary background.** League's brand lives in flat, saturated fills — the opposite of the "generic SaaS purple-to-pink gradient."

### Type
- **Single family: Inter Tight.** All 18 weights shipped. Display copy uses 800/900 with tight tracking (-0.02 to -0.035em). Body uses 400/500.
- **Hierarchy comes from weight + scale**, not color. A single weight jump reads stronger than adding color.
- **Tight letter-spacing on display.** This is key — Inter Tight is already condensed; we push tracking further negative on big sizes.
- **Eyebrows (ALL CAPS, purple, 12px, 0.12em tracking)** are the one decorative type treatment used. They signal section starts.

### Shape language
- **Hard squares + generous rounding.** The logo glyph is pure hard-corner squares. On-screen, we pair that with soft 10–16px radii on cards, 6–10px on buttons, 999px pills for tags. The contrast (hard brand mark over softly-rounded surfaces) is the signature.
- **Grid alignment.** Everything lives on a 4px base grid.
- **Generous whitespace.** League marketing is never cramped. Hero sections use 80–120px vertical rhythm.

### Backgrounds & imagery
- **Flat colour blocks** are the default. White for editorial, `--gray-50` for pages with lots of content, `--league-navy` for feature/hero dark sections.
- **Full-bleed photography** is used on marketing — warm-but-neutral tones, medium-close portraits of real people (patients, clinicians, parents), shot with natural light. Avoid cold, clinical stock photography; League leans human.
- **No hand-drawn illustrations** in the brand. No mascots, no character art.
- **Geometric accent shapes** — the logo's square motif is sometimes used as a decorative repeating element (offset squares in Blurple Mid or white at ~15–22% opacity), but restrained. **Never teal** — the squares are inspired by the logo, not recolored from it.
- **No textures, no grain, no film effects.** Imagery is clean and sharp.

### Motion
- **Calm, purposeful.** `cubic-bezier(0.2, 0.8, 0.2, 1)` (standard) or `(0.2, 0.9, 0.1, 1)` (emphasized).
- Durations: 120ms (micro), 200ms (default), 320ms (page / modal).
- **Fades and gentle slides (8–16px).** No bounces. No wobble. No spring overshoot.
- Hover = **subtle**: small lift (`translateY(-1px)`), shadow step up, or 6–8% darken. Never scale > 1.02.

### Interaction states
- **Hover (buttons, primary):** darken fill one step (`--purple-500` → `--purple-600`), add shadow-brand.
- **Hover (buttons, secondary):** background `--purple-50`, border unchanged.
- **Press / active:** darken one additional step; no translate-y.
- **Focus-visible:** 3px outline at `rgba(80, 28, 210, 0.35)`, offset 2px. Always visible; never suppressed.
- **Disabled:** 50% opacity + `cursor: not-allowed`. Don't grey-shift colors.

### Borders, shadows, elevation
- **Borders** are used generously — `1px solid var(--border)` (`#E8E6EE`) on cards, inputs, chips. Stronger `--border-strong` for hover/active.
- **Shadows** are **blue-cast** (navy-tinted), never pure black. Five-step scale (xs → xl) plus `--shadow-brand` (purple glow) for primary CTAs at rest only, not permanently.
- **Cards:** 1px border + 16px radius + shadow-sm at rest. Shadow-md on hover. No heavy drop shadows.
- **Elevation is not stacked** — either flat (border only), raised (shadow-sm), or prominent (shadow-lg for modals / hero cards). Rarely three levels in one view.

### Layout
- Max content width: **1200px** for standard product pages, **1440px** for marketing.
- **Fixed nav on top** (64px height), sometimes with a secondary sub-nav (48px). No sidebar on marketing; sidebar in product.
- **Bento-grid hero compositions** — League's marketing uses asymmetric card grids with one hero tile + smaller feature cards.
- **Two-column "statement + evidence"** is a dominant pattern: big headline left, quantified proof right.

### Transparency & blur
- Used **sparingly**. Glassy effects appear only on overlay nav (on scroll: `backdrop-filter: blur(12px)` + `rgba(255,255,255,0.72)`).
- **No frosted panels over photos.** If photo + text, use a solid or 90%-opacity panel.

### Corner radii
- 4 / 6 / 10 / 16 / 24 / 32 / 999px scale.
- Default: **10px** for controls, **16px** for cards, **pill** for tags/chips, **24–32px** for large feature tiles.

### Cards
- White surface, `1px solid var(--border)`, `border-radius: 16px`, `box-shadow: var(--shadow-sm)`, `padding: 24–32px`. Hover → `--shadow-md` and border shifts to `--border-strong`. That's the canonical card.

---

## ICONOGRAPHY

League does **not** appear to ship a proprietary icon font. Product and marketing surfaces use a **thin-to-medium-weight line icon set** with rounded joins — matching the style of **Lucide** / Feather very closely. That's the substitution we recommend and flag here:

- **Substituted icon set:** [Lucide](https://lucide.dev/) (`lucide-static` / CDN). Stroke width 1.75–2px, rounded caps and joins. Use at 16, 20, 24px. Consistent visual weight with Inter Tight body copy.
- **Why Lucide:** closest match to League's on-site iconography (see e.g. healthcare category nav, feature-card icons). Stroke geometry, radius of corners, and outline-only style align.
- **FLAG:** If League publishes a proprietary icon library, swap Lucide for that set. Icon semantics should carry over 1:1 for the common set (search, menu, chevrons, user, heart, shield, check, arrow-right, plus, close, calendar, bell, settings).

Rules:
- **Outline style only.** Avoid filled icon variants except inside success/error pills.
- **Match icon color to surrounding text** (`currentColor`) in 95% of cases. Use `--blurple-mid` only when the icon is the primary subject (e.g. feature card glyph). **Never color an icon teal** — teal is logo-only.
- **No emoji** on product or brand surfaces. No unicode stand-ins (✓, ★, →) — use proper icons.
- **Illustrations:** none in this system. Empty-states currently use the **glyph logo at low opacity** or an oversized Lucide icon in brand color. If you need full illustrations, ask the user — they should be commissioned, not AI-generated.

### Load from CDN
```html
<script src="https://unpkg.com/lucide@latest"></script>
<script>lucide.createIcons();</script>
```

---

## Font substitution note

All 18 Inter Tight TTFs are included in `fonts/`. No substitution was required. If you ever need to fall back: Inter → system-ui → sans-serif (defined in `--font-sans`).

---

## For iteration

This is a v1 draft. The highest-value things to verify or supply next:
1. **Canonical Figma library** or production CSS from the League Health OS — would let us pin exact component spec (buttons, inputs, cards, data viz).
2. **Product screenshots / login-protected UI** so we can build a proper UI kit for the member app + admin console.
3. **Sanctioned color palette** — the brand extensions (tonal scales, neutrals, semantic status colors) are derived, not documented; any internal palette overrides should replace the scales in `colors_and_type.css`.
4. **Icon set confirmation** — verify or replace the Lucide substitution.
5. **Illustration / photography direction** — samples of real League-approved imagery to reference.
