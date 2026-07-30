# Career Navigator — Design Guide v1 · "Trail Map"

The design system used across the Career Navigator prototype. Everything in
`index.html` derives from this guide; change the guide first, then the code.

## 1. Brand idea

**A career comeback is a hike, not an elevator.** The product draws the route,
marks the next waypoint, and plants a flag at the summit. Every visual choice
comes from that world: paper like a folded map, contour lines like terrain,
footprint-dotted trails, waypoint nodes, and one gold flag that means
*success*.

The personality is a **warm, confident guide** — never a corporate dashboard,
never a childish game. Our users (returners, immigrants, restarters, career
switchers) arrive anxious; the design's job is to make the journey look
finite, concrete, and started.

## 2. Logo

The mark: a **mint rounded-square tile** with a dark stair-stepped path
climbing from bottom-left, ending in a flagpole with a **gold pennant**.
Generated as brand art (see repo history), recreated in the site as inline
SVG so it stays crisp and theme-aware.

- Clear space: keep at least ½ tile-width empty around the mark.
- Wordmark: "Career" in ink + "Navigator" in mint, set in Bricolage Grotesque 800.
- Never: rotate the mark, recolor the flag, or place the tile on mint
  backgrounds (it needs contrast to read).

## 3. Color

One saturated brand color (mint), one success color (gold), everything else
is quiet. Gold is *earned* — reserve it for goals, progress, and primary
"start" actions. Don't use mint and gold at equal visual weight in the same
component.

### Light — "Daylight trail"
| Token | Hex | Use |
|---|---|---|
| `--paper` | `#F7F4EB` | page ground (warm paper) |
| `--paper-soft` | `#EFEBDD` | alternate strips, drawer header |
| `--card` | `#FFFEF8` | cards, nodes (steps) |
| `--ink` | `#1E2B26` | text, borders, offset shadows (pine charcoal) |
| `--muted` | `#5D6B64` | secondary text |
| `--mint` | `#4EC7A5` | brand: logo tile, primary buttons, selected states |
| `--mint-deep` | `#2E9C7D` | links, tags, eyebrows (AA on paper) |
| `--mint-soft` | `#DDF2E9` | tinted surfaces, AI-coach tips |
| `--gold` | `#F7C948` | flags, progress fill, "start/next" CTAs, done button |
| `--gold-soft` | `#FBEDC2` | next-step card surface |
| `--node` | `#FFD95E` | roadmap milestone nodes |
| `--done` | `#2E9E6B` | completed checkmarks |

### Dark — "Night trail"
Same hues on deep pine: `--paper #101915`, `--card #18251F`,
`--ink #EDEAE0`, `--edge #0A100D` (chunky borders/shadows),
`--mint-deep` brightens to `#6BDBBB` for link contrast. Mint, gold, and node
yellow stay identical — the brand colors never change between themes.

Theme mechanics: tokens on `:root`, redefined under
`@media (prefers-color-scheme: dark)`, then again under
`:root[data-theme="dark"]` / `:root[data-theme="light"]` so the in-page
toggle always wins.

## 4. Typography

| Role | Face | Notes |
|---|---|---|
| Display (h1–h3, node milestones, quiz questions) | **Bricolage Grotesque** 700–800 | embedded as woff2 data URI — no CDN dependency; characterful, warm, slightly quirky |
| Body | Avenir Next / Segoe UI system stack | 16px/1.6, comfortable for anxious readers |
| Wayfinding (eyebrows, tags, meta, legends) | ui-monospace stack | uppercase, letter-spaced `.1–.16em` — the "map annotation" voice |

Rules: body text ≤ ~65ch; `text-wrap: balance` on headings;
`tabular-nums` wherever digits align. Key phrases in headlines can take the
gold **marker highlight** (`mark.hl` — a gold band behind the lower half of
the text). One highlight per headline, maximum.

## 5. Tactile component language (neobrutalism-lite)

Every interactive element feels like a physical marker on the map:

- **Borders**: 2px solid `--edge` (2.5px for milestones/featured).
- **Offset shadows**: hard, no blur — `3px 3px 0 var(--edge)` for
  interactive elements, `4px 4px 0 rgba(ink, .12)` (softer) for static cards.
- **Hover**: element lifts `translate(-2px,-2px)` and the shadow grows to
  `5px 5px`. Active presses down (`translate(1px,1px)`, `2px 2px` shadow).
- **Link cards** hover with a **mint** solid shadow — color signals "this
  navigates".
- Corner radius 10–14px everywhere: chunky but friendly, never sharp.
- Restraint rule: chunky borders on *components*, hairlines (`--line`)
  never mix with them on the same element. Generous whitespace between
  bordered elements is mandatory — the style collapses when crowded.

## 6. Motifs & graphics

- **Topographic contours**: subtle SVG pattern (`--topo`, ~5% ink opacity)
  on hero and alternate strips only — never behind dense text blocks.
- **Footprint trails**: dotted connector lines use `stroke-dasharray: 1 7`
  with round caps — footsteps, not dashes. Used in the hero mini-map and
  roadmap wires.
- **Waypoints**: roadmap milestones are gold nodes; steps are paper cards;
  timeline dots are gold circles with edge borders.
- **The flag**: gold pennant marks success — logo, section eyebrows
  (`::before` triangle), footer, "trail complete" state. Never use it
  decoratively on unfinished things.

## 7. Motion

Motion says "the map is alive", never "look at me". All motion is disabled
under `prefers-reduced-motion`.

- **Reveal**: sections' cards fade-up 14px over .5s when scrolled into view
  (IntersectionObserver, `.reveal` → `.in`).
- **Pop-in**: roadmap and mini-map nodes scale in (.38s, slight overshoot)
  with a 35ms stagger, capped at 700ms total.
- **Micro**: button/node lift on hover (.1s); pennant nudge on logo hover;
  progress bar fill animates width.
- Budget: one orchestrated moment per view. No parallax, no looping
  animation, no motion on body text.

## 8. Voice & honesty

- Second person, plain words, confident warmth: "You didn't take years off —
  you ran a household."
- Every number shown must be real (counts of actual content) or explicitly
  labeled *sample/illustrative*. No fake precision: match scores are
  qualitative bands ("Strong match"), not percentages.
- The product never blames the user for the gap; copy frames setbacks as
  terrain ("the dip is part of the trail").
- One next step at a time: every journey view leads with a single
  gold-highlighted next action, not the full list.

## 9. Accessibility commitments

- Text contrast ≥ 4.5:1 in both themes (mint-deep, not mint, for text).
- Focus: 3px mint `:focus-visible` outline on everything interactive.
- Done-state is triple-encoded: check badge + dimming + progress counter.
- Drawer closes on Esc and backdrop click; roadmap nodes are real buttons.
- Known debt (fix before partner demos): drawer focus trap + focus return,
  keyboard order following the visual journey, mobile-first roadmap layout.

## 10. Don't

- Don't add a third accent color; don't use gold for anything sad.
- Don't put chunky borders on text paragraphs or the page body.
- Don't use blur shadows, gradients on buttons, or pure black/white.
- Don't animate more than one thing per interaction.
- Don't write "users" in UI copy — say "you".
