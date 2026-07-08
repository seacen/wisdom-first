# wisdom-first — Brand

One image carries the whole brand: **a golden diamond of wisdom rising out of a thin open book**. It states the product's promise — reach for humanity's best thinking *first*, then do the work — and every rule below exists to keep that image sharp.

## 1 · What the brand stands for

- **Promise**: an AI that makes you wiser, not more dependent. Every answer doubles as a lesson; the user keeps the mental models and the reading list.
- **Character**: a well-read advisor — grounded in canonical books, warm on human problems, plain-spoken.
- **Never**: lightbulbs, owls, brains, sparkles, gradients — the stock imagery of "smart AI" is exactly what this brand is not.

## 2 · The mark

A thin open book with a gilt fore-edge; a marquise-cut diamond rises from its spine, taller than the book itself. One shape, three reads:

| Layer | What you see | What it means |
| --- | --- | --- |
| Gold | two gilt edges + the diamond's peak — high, low, *higher*, low, high | the skeleton of a **W** (wisdom) |
| Ink | two thin boards tapering into a spine gutter | the open book: the canon the skill reaches for |
| Whole | the diamond's body above the book, its tip still in the gutter | wisdom drawn out of the book *before* the work — "first" |

Geometry to preserve when reproducing: boards slope ~42° and taper toward the spine; diamond apex is 43° — never sharper; the diamond is always the highest point; its tip stays inside the gutter (the gem comes *out of* the book, it is not pasted above it).

## 3 · Color

Ink + paper + one gold. Never more than one gold per surface; no gradients, shadows, or outlines.

| Token | Hex | Role |
| --- | --- | --- |
| Ink | `#1B2C40` | book boards and wordmark on light; body text on light |
| Paper | `#F5F1E6` | light ground |
| Deep | `#101C2B` | dark ground |
| Paper-on-dark | `#EFE8D8` | book boards and wordmark on dark |
| Gilt (light) | `#B8862F` | gold of the mark on light grounds |
| Gilt (dark) | `#E3B054` | gold of the mark on dark grounds |
| Text gold | `#96690F` | "-first" in the wordmark on light (contrast-safe) |

## 4 · Typography

- **Wordmark**: Source Serif 4 (SIL OFL), `wght 580 / opsz 24`, all lowercase to match the package name (`npx skills add seacen/wisdom-first`), fi ligature on, "-first" set in gold. It ships as outlined paths in `assets/logo/` — use those files, never re-set it live.
- **Everything else**: a book serif for display (Source Serif 4), the platform's default sans for UI. Type stays quiet; the mark carries the identity.

## 5 · Using the assets

All files live in [`assets/logo/`](assets/logo/) — light/dark, SVG/PNG, with and without the wordmark, plus single-color versions; build details in its [README](assets/logo/README.md).

- Pick the variant made for your background; never recolor.
- Clear space: at least ¼ of the mark's height on all sides.
- Minimum sizes: mark 16 px, wordmark lockup 140 px wide.
- Don't stretch, rotate, add effects, or re-set the wordmark in another font.

## 6 · Voice

Write the way the skill answers: name the actual framework, cite the actual book, give the few moves that matter, and lead with warmth on human problems. Plain words, no hype — the authority comes from the sources, not from adjectives.
