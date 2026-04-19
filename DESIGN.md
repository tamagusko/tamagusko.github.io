# Design System — Personal Site for a Researcher in Mobility, Computer Vision & Urban AI

## 1. Visual Theme & Atmosphere

This system inherits the discipline of Ollama's radical minimalism and reshapes it for a researcher's public site. The foundation is still "every pixel earns its place" — but the voice shifts from pure digital tool to something closer to a **well-kept field notebook**: legible, durable, unhurried. Heritage tech and wabi-sabi minimalism — paper and ink rather than screen and pixel — without losing the confidence of a modern system.

Where Ollama is pure white + pure grayscale, this system warms the canvas: **bone-white backgrounds (the color of good writing paper) and ink-black text**. Grayscale still dominates roughly 95% of the surface area, but the neutrals are warm rather than clinical — the difference between fluorescent office light and an afternoon reading room.

The site allows a single restrained chromatic note: **deep ink navy**, used only for primary links, the author's name in the masthead, and a small number of accents — never as a brand color, never as decoration. It reads as the color of a fountain pen, not a product palette.

What distinguishes this system from Ollama's is the **three-voice typography**: a serif display face for headings (heritage, academic authority), a clean system sans for body text (modern readability), and monospace for numeric data, coordinates, metrics, and code. A researcher working across pavement measurements, detection scores, and model identifiers needs monospace as a functional tool — not a stylistic one.

**Key characteristics**

- Bone-white canvas (warmer than pure white) with ink-black text
- Three-voice typography: serif headings, sans body, monospace for data
- Binary border-radius: 6px containers, 9999px pills — tighter than Ollama to feel more "print"
- Zero shadows — depth from background shifts and hairline borders only
- Pill-shaped interactive elements (buttons, tags, filter chips)
- A single restrained accent (Ink Navy) for primary links and focus
- Simple ink linework permitted as illustration (road networks, cycling routes, bounding-box diagrams) — never photography-heavy
- Content density is low by design — the homepage presents the person, their current work, and a short list of deep links; nothing more

## 2. Color Palette & Roles

### Primary
- **Ink Black** (`#14110F`): Primary text, headlines, body. Slightly warm — not pure black, not charcoal.
- **Ink Navy** (`#1B3A5B`): The single chromatic accent. Primary links, masthead name, focus states.
- **Graphite** (`#2E2A26`): Button text on light surfaces, secondary headline weight.

### Surface & Background
- **Bone** (`#F7F4EE`): The primary page background — warm, paper-like. Never pure white.
- **Parchment** (`#EFEAE0`): Subtle surface distinction for section backgrounds and tinted hover states.
- **Page White** (`#FDFBF6`): The lightest surface — used for card backgrounds when contrast against Bone is needed.

### Neutrals & Text
- **Stone** (`#6B655C`): Secondary body text, metadata (dates, venues, authors), de-emphasized content.
- **Mid Stone** (`#4D4843`): Emphasized secondary text.
- **Silver** (`#9A958B`): Tertiary text, placeholders, separators.
- **Faint Line** (`#D9D3C6`): Borders and hairlines — warmer than cool gray, almost invisible until it needs to be.

### Semantic & Accent
- **Ink Navy** (`#1B3A5B`): Primary links, the author's name in the masthead, focus rings (at ~40% opacity).
- **Moss** (`#5A6A47`): An optional second accent, reserved for cases where Ink Navy is already occupied (e.g., an "active project" badge alongside a navy link). Used sparingly or not at all.

### Gradients
**None.** Flat color blocks and hairline borders carry all visual separation. Gradients break the paper-like surface; avoid them entirely.

## 3. Typography Rules

### Font Family
- **Display (headings, name)**: `EB Garamond` with fallbacks `'Source Serif Pro', 'Iowan Old Style', Georgia, Cambria, 'Times New Roman', serif`
- **Body / UI**: `Inter` with fallbacks `system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif`
- **Monospace**: `'JetBrains Mono'` with fallbacks `ui-monospace, SFMono-Regular, Menlo, Consolas, monospace`

*Rationale: A transitional serif for display carries academic heritage. System sans maximises readability on long publication lists. Monospace handles coordinates, IRI values, mAP scores, DOIs, and code — all content a transport / computer-vision researcher actually works with.*

### Hierarchy

| Role | Font | Size | Weight | Line Height | Notes |
|------|------|------|--------|-------------|-------|
| Display Name / Hero | Serif | 44px (2.75rem) | 500 | 1.10 | Author's name, site title |
| Page Heading | Serif | 34px (2.125rem) | 500 | 1.15 | Section titles (Publications, Projects) |
| Sub-heading | Serif | 24px (1.5rem) | 500 | 1.25 | Project names, paper titles on index |
| Card Title | Sans | 18px (1.125rem) | 500 | 1.35 | List item titles, nav emphasis |
| Body Large | Sans | 18px (1.125rem) | 400 | 1.60 | Lede paragraphs, hero description |
| Body | Sans | 16px (1rem) | 400 | 1.60 | Standard prose, reading text |
| Meta | Sans | 14px (0.875rem) | 400 | 1.45 | Dates, venues, author lists |
| Caption | Sans | 13px (0.8125rem) | 400 | 1.40 | Figure captions, fine print |
| Code / Data | Mono | 14px (0.875rem) | 400 | 1.55 | Coordinates, metrics, identifiers, DOIs |
| Tag / Badge | Sans | 12px (0.75rem) | 500 | 1.30 | Filter pills, domain tags (tracked uppercase) |

### Principles
- **Serif headings, sans body, mono for data**: Three voices, each with a role. The serif signals heritage and authority; the sans keeps reading effortless; the mono signals precision.
- **Weight restraint**: 400 (regular) and 500 (medium) only. No bold, no thin, no black — as in Ollama, but with two weights across three families.
- **Generous line-height for reading**: Body copy lands at 1.60 — abstracts and long-form pages need room to breathe.
- **Tracked uppercase for tags**: Labels like `COMPUTER VISION` or `URBAN MOBILITY` use roughly 0.08em letter-spacing, sans 500.
- **Italic serif for titles of works and venues**: Following academic convention — paper titles and journal names in italic serif, never in sans.

## 4. Component Stylings

### Buttons

**Filled Pill (Primary / CTA)**
- Background: Ink Black (`#14110F`)
- Text: Bone (`#F7F4EE`)
- Padding: 10px 22px
- Radius: pill (9999px)
- Use: "Download CV", "Contact", "Read paper"

**Outline Pill (Secondary)**
- Background: transparent
- Text: Ink Black
- Border: 1px solid Faint Line (`#D9D3C6`)
- Padding: 10px 22px
- Radius: pill (9999px)
- Use: "View code", "Preprint", "DOI"

**Text Link (Default)**
- Color: Ink Navy (`#1B3A5B`)
- Underline: 1px, offset 3px
- Hover: underline thickens to 2px, no color change
- External links carry a small ↗ glyph at 0.7em

### Cards & Containers

**Publication Row** — the primary content unit of the site
- Not a card — a bordered row, separated by a 1px Faint Line rule on top, no background fill
- Padding: 20px 0
- Structure (left to right): **Year** in mono 14px Stone (fixed ~60px column) | **Title** in serif 18px Ink Black (italicised for the paper title) | **Venue** in italic serif Stone 15px | **Meta row** with domain tag pills, author list, DOI/PDF/BibTeX actions in Ink Navy
- Hover: background tints to Parchment (`#EFEAE0`) across the full row width, no shadow

**Project Card**
- Background: Page White (`#FDFBF6`)
- Border: 1px solid Faint Line
- Radius: 6px
- Padding: 24px
- Structure: project name (serif 24px, 500) · 2-line description (sans 16px) · 3–4 tag pills · footer link row ("Paper", "Code", "Project site")

**Quote / Blockquote**
- Left border: 2px solid Ink Navy
- Padding-left: 20px
- Style: italic serif, Stone colour
- Use: invited talks, endorsements, notable citations

**Citation Block**
- Background: Parchment (`#EFEAE0`)
- Text: monospace 13px Stone
- Radius: 6px
- Padding: 16px
- "Copy BibTeX" pill button floats top-right

### Inputs & Forms
- Background: Page White
- Border: 1px solid Faint Line
- Radius: pill (9999px) for single-line fields; 6px for textareas
- Focus: 2px Ink Navy ring at ~40% opacity
- Placeholder: Silver

### Navigation
- Transparent background on Bone, no border, no fill
- Left: author's name in serif 20px weight 500, Ink Navy
- Right: 4–5 text links in sans 15px weight 400 Ink Black (suggested: Research · Writing · Teaching · About · CV)
- No search bar — this is a personal site, not a catalogue
- On scroll: nav sticks; background solidifies to Bone with a 1px Faint Line bottom hairline

### Image Treatment
- Photography is allowed but rare — a single portrait is the outer limit. Render in warm grayscale, never saturated.
- **Preferred illustration**: simple ink linework — road-network fragments, cycling-route traces, bounding-box diagrams from CV work, small technical figures from papers. Black ink on Bone.
- Figures from papers retain their academic styling — serif captions below, mono for labels.
- No stock photography. No gradient overlays. No 3D renders.

### Distinctive Components

**Filter Chips (Publications)**
- Pill-shaped (9999px), 8px 14px padding
- Inactive: transparent background, 1px Faint Line border, Stone text
- Active: Ink Black background, Bone text, no border
- Typical filters: `Pavement`, `Computer Vision`, `VLM`, `Urban Mobility`, `Cycling`, `Aviation`, plus years

**Year Rail / Jump Index**
- Thin vertical rail on the Publications page: years listed in mono 14px Stone
- Current year on scroll: Ink Black weight 500
- Quick navigation through a long list without reloading

**Domain Tag**
- Small pills (9999px), 2px 10px padding, sans 12px tracked uppercase
- Transparent background with Faint Line border
- Labels the research domain of a paper or project (`VLM`, `YOLOv11`, `LTPP`, `REALLOCATE`, `COLOURWAYS`)

**"Now" Strip / Currently Working On**
- A single-line rule-and-dot sequence on the About page
- Ink Navy dot on a Faint Line rule, with short monospace captions ("Oct 2026 — REALLOCATE field pilot")
- Serves as a lightweight status indicator without becoming a feed

## 5. Layout Principles

### Spacing System
- Base unit: 4px
- Scale: 4, 8, 12, 16, 20, 24, 32, 40, 56, 80, 120px
- Section vertical spacing: 80–120px (generous — emptiness as luxury)
- Card padding: 24px
- Publication row vertical padding: 20px

### Grid & Container

Three content widths, each with a purpose:

- **Reading width — 720px**: About, individual paper pages, blog posts. Optimised for prose; body text tops out around 65 characters per line.
- **Index width — 960px**: Publications, Projects, Teaching. Allows a filter sidebar plus a list column.
- **Hero width — 1100px**: Homepage only. Slightly wider to breathe.

All centred, with symmetric gutters.

### Whitespace Philosophy
- **Whitespace as pause**: Academic writing rewards slow reading. Every section has clear breathing room above and below.
- **Low content density**: The homepage presents the person, one paragraph on current research, three featured projects, and the most recent publications. Nothing more.
- **Short reading measure**: Body text caps around 65 characters per line regardless of viewport width.

### Border Radius Scale
- **6px** — containers, cards, code blocks, image frames, textareas
- **9999px** — pills: buttons, tags, filter chips, avatar

*Nothing in between.* No 4px, no 10px, no 16px. The binary system holds.

## 6. Depth & Elevation

| Level | Treatment | Use |
|-------|-----------|-----|
| Flat (Level 0) | No shadow, no border | Page background, body prose |
| Hairline (Level 1) | `1px solid #D9D3C6` | Publication rows (top rule), cards, outline buttons |
| Tinted (Level 2) | Parchment (`#EFEAE0`) background, no border | Section differentiation, row hover, citation blocks |

**Shadow philosophy**: Zero shadows. The Bone background already supplies a papery atmosphere — a shadow would turn it into a product page. Depth comes from background shifts (Bone → Parchment → Page White) and hairline rules.

## 7. Do's and Don'ts

### Do
- Use Bone (`#F7F4EE`) as the page background — warm, paper-like, never pure white
- Use the serif for headings, the masthead name, and paper titles — the heritage signal
- Use monospace for all numeric data: coordinates, IRI values, mAP scores, DOIs, dates in metadata rows
- Use Ink Navy sparingly, only for primary links, focus rings, and the masthead
- Keep the binary radius system — 6px containers, pill interactives — absolute
- Keep the homepage short; let the Publications and Projects indexes do the heavy lifting
- Use tag pills to label research domains — they are the primary wayfinding across the site
- Italicise paper titles and venue names — standard academic convention
- Use simple ink linework for any illustration — road networks, bounding boxes, cycling traces

### Don't
- Don't use pure white (`#ffffff`) — the Bone warmth is a defining feature
- Don't introduce a second chromatic hue without a clear reason — Ink Navy is the single accent
- Don't add shadows — ever
- Don't use radii between 6px and 9999px — the binary is absolute
- Don't use weights above 500 — no bold, no black
- Don't use stock photography or AI-generated imagery
- Don't use colour to signal research domain — use tag text and italics instead
- Don't overcrowd the homepage — three featured items per section is the ceiling
- Don't use gradients, glows, or glassmorphism

## 8. Responsive Behaviour

### Breakpoints

| Name | Width | Key changes |
|------|-------|-------------|
| Mobile | <640px | Single column; nav collapses to hamburger or bottom bar; filter chips scroll horizontally |
| Tablet | 640–900px | Reading pages unchanged; index pages drop filter sidebar to a top row |
| Desktop | 900–1100px | Standard layout; filter sidebar on index pages |
| Wide | >1100px | Homepage hero widens; reading pages still cap at 720px |

### Reading Width Always Caps
No matter how wide the viewport, body prose never exceeds 720px. Wide monitors receive more margin, not more line length.

### Touch Targets
- All pills: 10px 22px padding comfortably exceeds 44×44px
- Publication rows: full-width tap zone
- Filter chips: horizontally scrollable on mobile, never wrapped to two rows

### Collapsing Strategy
- **Navigation**: desktop horizontal → mobile hamburger or bottom bar
- **Publications index**: sidebar filters → top filter row on tablet → horizontal-scroll chips on mobile
- **Project grid**: 2-column → single column
- **Hero typography**: 44px → 36px → 30px progressive scaling

## 9. Dark Mode (Optional)

A restrained night variant, for users on dark system settings:

- Background: Ink Black (`#14110F`) — not pure black
- Text: Bone (`#F7F4EE`)
- Surfaces: `#1D1916` (cards), `#221E1A` (tinted sections)
- Hairlines: `#3A342E`
- Accent: Pale Navy (`#9BB4D1`) — lifted from Ink Navy for contrast on dark
- All other principles hold: binary radius, pills, no shadows, no gradients

## 10. Agent Prompt Guide

### Quick Colour Reference
- Primary Text: "Ink Black (#14110F)"
- Page Background: "Bone (#F7F4EE)"
- Card Surface: "Page White (#FDFBF6)"
- Tinted Surface: "Parchment (#EFEAE0)"
- Secondary Text: "Stone (#6B655C)"
- Muted Text: "Silver (#9A958B)"
- Borders / Rules: "Faint Line (#D9D3C6)"
- Accent / Links: "Ink Navy (#1B3A5B)"

### Example Component Prompts

- "Create a hero section on Bone (#F7F4EE). Author's name in EB Garamond 44px weight 500 Ink Navy (#1B3A5B). Below, a one-paragraph research statement in Inter 18px weight 400 line-height 1.6, Ink Black (#14110F). Add a black pill button (9999px radius, 10px 22px padding) 'Read recent work' and an outline pill 'Download CV' with a 1px Faint Line (#D9D3C6) border."

- "Build a publication row. Top border 1px solid Faint Line (#D9D3C6). Left column: year in JetBrains Mono 14px Stone (#6B655C), fixed ~60px width. Main column: paper title in italic EB Garamond 18px Ink Black, then venue in italic Stone 15px, then a meta row with domain tag pills (uppercase Inter 12px tracked 0.08em, transparent background with Faint Line border) and DOI link in Ink Navy. Hover fills the full row with Parchment (#EFEAE0). No shadow."

- "Design a project card for a VLM research project. Page White (#FDFBF6) background, 1px solid Faint Line border, 6px radius, 24px padding. Title 'COLOURWAYS' in EB Garamond 24px weight 500. Two-line description in Inter 16px Ink Black. Footer row with 3 tag pills ('VLM', 'URBAN MOBILITY', 'UCD') and a right-aligned 'View project' link in Ink Navy."

- "Create a filter chip row for the publications page. Chips are pill-shaped (9999px radius), 8px 14px padding. Inactive: transparent background, 1px Faint Line border, Stone text. Active: Ink Black background, Bone text, no border. Domain filters: Pavement, Computer Vision, VLM, Urban Mobility, Cycling, Aviation."

- "Design a citation block for a paper detail page: JetBrains Mono 13px Stone text on Parchment (#EFEAE0) background, 6px radius, 16px padding. 'Copy BibTeX' pill button floats top-right with Ink Black background and Bone text."

- "Navigation: transparent background on Bone, no border. Left: author's name in EB Garamond 20px weight 500 Ink Navy. Right: text links (Research, Writing, Teaching, About, CV) in Inter 15px weight 400 Ink Black. On scroll, background solidifies to Bone with a 1px Faint Line bottom border."

### Iteration Guide
1. Reach for the serif first for any heading, masthead, or title of a work
2. Monospace is for numbers, identifiers, and code — never for decoration
3. Ink Navy should appear on a page a dozen times at most — treat it as precious
4. Three surfaces only: Bone (page), Page White (cards), Parchment (tinted). No more.
5. If you're tempted to add a shadow, add a hairline border or a Parchment tint instead
6. If a page feels decorated, strip a tag, an icon, or a divider — it should read like a well-set page of a journal
