# Sunday Batch — Design System
Plant-based bowls, salads and breakfasts. The reader is planning a week, not
cooking one dinner, and the layout should say which things matter most.

## 1. Colour

| Token | Hex | Role |
|---|---|---|
| `--ink` | `#3C2A3E` | Aubergine. All text |
| `--ground` | `#FBFAF6` | Page |
| `--surface` | `#D6E0CE` | Pale sage. Tile fill |
| `--brand` | `#4E7A46` | Matcha. Link and button text |
| `--accent` | `#E9A26B` | Apricot. **Tile fill only, never text** |
| `--rule` | `#E4E7DE` | The few hairlines there are |
| `--muted` | `#645266` | Derived secondary text |

**Contrast, measured:**
- `--ink` on `--ground` = **12.62:1** (AAA)
- `--ink` on the sage tile = 9.68:1 (AAA) · on the apricot tile = **6.18:1** (AA+)
- `--brand` matcha on ground = **4.79:1** (AA) — which is what buttons and
  links use, and it is why the button is matcha *text* rather than a matcha
  fill.
- **Matcha on a sage tile is only 3.67:1**, so matcha text never appears on a
  tile. Text on tiles is always aubergine.
- **Apricot on ground is 2.04:1.** It is a fill colour and nothing else.
- `--muted` on ground = 6.84:1.

## 2. Type

*Outfit* 500/700 — headings. A geometric sans.
*Petrona* 400 — body. A serif.

**This is the inverse of the usual pairing** and it is the deliberate choice of
the site: almost every food blog runs a serif display over a sans body, so
running a geometric sans display over a serif body reads as a different kind of
publication immediately.

Scale ratio **1.250**.

```css
--step--1: clamp(0.88rem, 0.86rem + 0.10vw, 0.92rem);
--step-0:  clamp(1.0625rem, 1.04rem + 0.12vw, 1.125rem);
--step-1:  clamp(1.25rem, 1.20rem + 0.25vw, 1.40rem);
--step-2:  clamp(1.50rem, 1.41rem + 0.44vw, 1.75rem);
--step-3:  clamp(1.85rem, 1.68rem + 0.80vw, 2.19rem);
--step-4:  clamp(2.20rem, 1.92rem + 1.35vw, 2.74rem);
--step-5:  clamp(2.60rem, 2.12rem + 2.30vw, 3.43rem);
```

- Body line-height **1.75**, measure **64ch**
- Headings 1.15, tracking −0.015em

## 3. Space

**Bento gutter `16px`** — tight, so the tiles read as a single composed block
rather than as separated cards. **Section rhythm `72px`.**

## 4. Shape

- **12px radius on tiles only. 0 on text blocks, images inside prose, tables
  and form fields.** Radius marks a tile and nothing else.
- **No shadows anywhere.** Tiles are separated from the page by their
  `--surface` or `--accent` fill, not by elevation. That is the whole
  mechanism.

## 5. Layout

An **asymmetric bento grid on four columns where tile size encodes
importance**. The featured recipe is 2×2. Quick ones are 1×1. Secondary ones
are 2×1. The meal-prep note is a full-width 4×1 band at the bottom.

**It is never a uniform card wall.** If every tile were the same size the grid
would be telling the reader nothing, and the whole point is that the shape of
the page is the editorial judgement.

```
┌───────────────┬───────┬────────────────┐
│               │ 1×1   │ 1×1            │
│   2×2 featured├───────┴────────────────┤
│               │ 2×1                    │
├───────┬───────┴────────────────────────┤
│ 2×1   │ 2×1                            │
├───────┴────────────────────────────────┤
│ 4×1  MEAL PREP: batch Sunday, keeps 4d │
└────────────────────────────────────────┘
```

At ≤900px the grid collapses to two columns and the featured tile stays 2 wide;
at ≤600px it becomes a single column in editorial order.

## 6. Components

- **Tile** — a flat `--surface` sage or `--accent` apricot fill, 12px radius,
  **no border and no shadow**. Image at the top, aubergine text beneath.
- **Nav** — one row, matcha underline on the current page.
- **Button** — **matcha text with a 2px underline that thickens to 4px on
  hover.** No box, no fill, no radius.
- **Nutrition block** — a plain two-column list, marked "estimate", with no
  tile fill and no decoration at all. It is deliberately the least designed
  thing on a recipe page.
- **Form field** — 0 radius, 1px `--rule`, ground fill.
- **Footer** — sage field, aubergine text.

## 7. The one memorable thing

**A meal-prep column on every recipe, in its own wide tile:** what to batch on
Sunday, exactly how long it keeps, and what to swap when you are bored of it by
Wednesday. It is the widest tile on every recipe page, because for the person
this site is for it is the most useful thing on it — the question is almost
never "how do I cook this once" but "how do I eat well on Thursday".

## Checked against the banned list
- Not cream + big serif + terracotta: the ground is a cool near-white, the
  display face is a geometric sans, and apricot appears only as a tile fill.
- No dark page with an acid accent.
- **Not a uniform rounded-card wall** — the tiles are deliberately different
  sizes, and there is no shadow on any of them, which is the specific banned
  combination.
- No tracked-out caps eyebrows, no `·` meta strings, no `→`, no coloured word
  inside a headline, no gradients, no emoji, no scroll animation. One
  transition, on the button underline.

## Sameness test
Against the other four recipe sites: Long Braise is oat and enamel blue with a
sticky ingredient rail and dark moody photography; Twenty Flat is mustard
colour-blocks with 3px navy rules and a giant time numeral; The Spice Base
is cotton and indigo with printed dividers and a single centred column; The
Bench Notes is graph paper and mono formula tables. This is the only bento
grid, the only site with any radius at all, the only sans-display-over-serif-body
pairing, and the only high-key marble photography.
