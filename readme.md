# Smidgen CSS

A featherlight, no-nonsense CSS grid and layout system built for speed and simplicity.

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-2.0-blue.svg)

---

## What's New in v2

- **Order utilities** — `order-first` and `order-last` with responsive variants
- **Flex direction utilities** — `flex-row` and `flex-row-reverse` with responsive variants
- **Responsive alignment** — `sm-align-*`, `md-align-*`, `lg-align-*` plus the same for `self-*`
- **Row-gap fix** — wrapped columns now have vertical space between them automatically
- **New `--wrapper-padding` variable** — control `.content-wrapper` padding without touching the CSS

v2 is fully backward compatible. No existing class names or behaviors changed.

---

## Why Smidgen CSS?

In a world of complex frameworks, Smidgen CSS is intentionally simple. It's a tiny, plain CSS file that provides the essential tools to create responsive layouts. There are no preprocessors, no JavaScript, and no complicated classes to memorize.

It's designed for developers who want to get a project up and running quickly while maintaining full control over their code.

### Features

- **Purely CSS**: No Sass, Less, or JavaScript required.
- **Incredibly Lightweight**: A tiny footprint for faster load times.
- **Mobile-First Design**: Naturally responsive, scaling up from mobile to desktop.
- **Flexbox-Powered**: Built on modern, powerful Flexbox for easy alignment and distribution.
- **Easily Customizable**: Tweak containers, gutters, padding, and breakpoints by changing a few CSS variables.
- **Essential Utilities**: Includes classes for containers, wrappers, gutters, alignment, ordering, and direction.

---

## Quick Start

1.  Download the `smidgen.min.css` file from this repository.
2.  Link it in the `<head>` of your HTML file.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Awesome Site</title>
    <link rel="stylesheet" href="path/to/smidgen.min.css" />
  </head>
  <body></body>
</html>
```

---

## How to Use

### The Basic Structure

The layout system consists of two main components: a `.content-wrapper` for full-width sections (like a background color) and a `.content-well` to constrain your content to a centered, max-width container.

```html
<div class="content-wrapper">
  <div class="content-well">... your grid goes here ...</div>
</div>
```

**Container Variations**:

- `.content-well-narrow`: For tighter content areas.
- `.content-well`: The standard, default width.
- `.content-well-wide`: For more spacious layouts.

### The Grid

To create a grid, use the `.flex-grid` container and fill it with `.flex-col` items. Add responsive classes to control the column widths at different breakpoints (`sm-`, `md-`, `lg-`).

To add spacing (gutters) between columns, simply add the `.with-gutters` class to the `.flex-grid` container. In v2, wrapped columns also get vertical spacing automatically.

```html
<div class="flex-grid with-gutters">
  <div class="flex-col sm-12 md-6">...</div>
  <div class="flex-col sm-12 md-6">...</div>
</div>
```

### Auto and Shrink Columns

For flexible columns, use `.col-auto` to make a column automatically fill the remaining space, or `.col-shrink` to make it only as wide as its content.

```html
<div class="flex-grid with-gutters">
  <div class="flex-col col-shrink">Shrink</div>
  <div class="flex-col col-auto">Auto</div>
  <div class="flex-col lg-3">lg-3</div>
</div>
```

### Alignment Utilities

Control the alignment of columns within a `.flex-grid` container or align individual columns themselves. All alignment utilities have responsive variants.

**1. On the `.flex-grid` container:**

- **Horizontal:** `.justify-start`, `.justify-center`, `.justify-end`, `.justify-between`, `.justify-around`
- **Vertical:** `.align-top`, `.align-middle`, `.align-bottom`, `.align-stretch`
- **Responsive:** prefix any of the above with `sm-`, `md-`, or `lg-` (e.g., `md-align-middle`, `lg-justify-between`)

```html
<div class="flex-grid align-middle justify-center">
  <div class="flex-col sm-4">...</div>
  <div class="flex-col sm-4">...</div>
</div>
```

**2. On an individual `.flex-col`:**

- **Vertical Self-Alignment:** `.self-top`, `.self-middle`, `.self-bottom`, `.self-stretch`
- **Responsive:** `sm-self-top`, `md-self-middle`, `lg-self-bottom`, etc.

```html
<div class="flex-grid align-top">
  <div class="flex-col sm-6">This column is tall.</div>
  <div class="flex-col sm-6 self-bottom">This column is at the bottom.</div>
</div>
```

### Order Utilities

Reorder columns visually without changing the source markup. Useful for layouts where you need a different stacking order on mobile than on desktop.

- `.order-first` — displays first
- `.order-last` — displays last
- **Responsive:** `sm-order-first`, `md-order-first`, `lg-order-last`, etc.

```html
<div class="flex-grid with-gutters">
  <div class="flex-col sm-12 md-6 order-last md-order-first">
    Image, shown last on mobile, first on desktop
  </div>
  <div class="flex-col sm-12 md-6">Text content</div>
</div>
```

### Flex Direction

Flip the direction of columns inside a `.flex-grid`. By default, grids flow left-to-right; `.flex-row-reverse` flips them right-to-left.

- `.flex-row` — default direction (use as a reset at a breakpoint)
- `.flex-row-reverse` — reverses horizontal order
- **Responsive:** `sm-flex-row-reverse`, `md-flex-row`, `lg-flex-row-reverse`, etc.

```html
<div class="flex-grid with-gutters flex-row-reverse md-flex-row">
  <div class="flex-col sm-6">...</div>
  <div class="flex-col sm-6">...</div>
</div>
```

---

## Customization

You can change the entire system by editing the CSS variables defined at the top of the `smidgen.css` file, or by overriding them in your own stylesheet.

```css
:root {
  --grid-gutter: 1.5rem;
  --wrapper-padding: 3rem;
  --container-narrow: 900px;
  --container-standard: 1140px;
  --container-wide: 1320px;
}
```

- `--grid-gutter` — horizontal and vertical spacing between columns when `.with-gutters` is used
- `--wrapper-padding` — top and bottom padding on `.content-wrapper`
- `--container-narrow` / `--container-standard` / `--container-wide` — max-widths for the three container sizes

---

## Upgrading from v1

Drop in the new `smidgen.min.css` and you're done. Every v1 class still exists and behaves the same way. The only visible change is that wrapped columns inside `.with-gutters` will now have vertical space between them — if your current layout relies on them touching, you can override `row-gap: 0` on specific grids.

---

## License

This project is licensed under the **MIT License**. See the `LICENSE` file for details.
