# wisdom-first — logo

A thin open book with a gilt fore-edge; a golden diamond rises from its spine, taller than the book itself — the wisdom you reach for *first*, before the work. Book edges and diamond together sketch the letter **W**.

## Files

| File | Use on | What it is |
| --- | --- | --- |
| `logo.svg` | light backgrounds | mark only — ink `#1B2C40` + gilt `#B8862F` |
| `logo-dark.svg` | dark backgrounds | mark only — paper `#EFE8D8` + gilt `#E3B054` |
| `logo-wordmark.svg` | light backgrounds | mark + "wisdom-first" wordmark |
| `logo-wordmark-dark.svg` | dark backgrounds | mark + wordmark |
| `logo-mono-ink.svg` | light, one-color print | single-color ink |
| `logo-mono-gold.svg` | dark, foil / watermark | single-color gilt |
| `png/` | anywhere SVG won't do | transparent PNGs — mark at 16–1024 px, wordmark at 600/1200/2400 px wide |

GitHub README pattern (auto light/dark):

```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/logo/logo-dark.svg">
  <img src="assets/logo/logo.svg" alt="wisdom-first" width="130">
</picture>
```

## Rules

- **Clear space**: keep at least ¼ of the mark's height empty on all sides.
- **Minimum size**: mark 16 px; wordmark lockup 140 px wide.
- **Colors are fixed**: ink `#1B2C40`, paper `#EFE8D8`, gilt `#B8862F` (light) / `#E3B054` (dark). One gold only — don't add gradients, shadows, or outlines.
- **Don't** recolor the center page, stretch the mark, rotate it, or set the wordmark in another font.

## Rebuilding

The wordmark is outlined from **Source Serif 4** (SIL OFL 1.1), instanced at `wght 580 / opsz 24`, shaped with HarfBuzz (kerning + fi ligature), then baked to fixed paths — the SVGs have no font dependency. PNGs are rendered from the SVGs with `rsvg-convert`.
