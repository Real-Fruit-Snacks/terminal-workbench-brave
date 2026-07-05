# Terminal Workbench for Brave

A Brave browser theme in two variants, ported from the [Terminal Workbench](THEME-SPEC.md) design system: layered green-graphite surfaces, a restrained mint accent on the active tab and bookmark bar, and otherwise quiet, high-contrast chrome.

| Package | Description |
|---|---|
| `dist/terminal-workbench-dark` | Graphite dark mode |
| `dist/terminal-workbench-light` | Pale sage light mode |

Both variants are generated from a single token source and meet WCAG AA contrast on every text and surface pair the theme controls.

## Installation

### From a release

1. Download the dark or light package from the [Releases](https://github.com/Real-Fruit-Snacks/terminal-workbench-brave/releases) page and extract it.
2. Open `brave://extensions` and enable **Developer mode** (top right).
3. Select **Load unpacked** and choose the extracted folder.

### From a clone

Follow steps 2–3 above, selecting `dist/terminal-workbench-dark` or `dist/terminal-workbench-light` directly from the repository.

The theme applies immediately; no restart is required.

## Switching and removing

Chromium allows one theme at a time. Loading the other variant replaces the current one. To return to the default appearance, remove the extension from `brave://extensions` or use *Reset to default* under `brave://settings/appearance`.

**New Tab Page:** Brave places its own background image over the New Tab Page by default. To see the theme's New Tab colors, open the New Tab Page customization menu and disable the background image.

## Customization

Every color lives in [tokens.json](tokens.json), keyed by design-token name for both modes. After editing:

```sh
node build.mjs
```

The build (Node.js 18 or later, no dependencies) regenerates both packages and enforces a WCAG contrast gate over every text/surface pair it emits — 4.5:1 for primary text, 3:1 for de-emphasized UI. It refuses to write output if any pair falls below its target. Reload the theme from `brave://extensions` to apply changes.

## Design

The theme follows the Terminal Workbench principle of *quiet chrome, loud signal*: near-monochrome surfaces spend color only where it carries meaning — the active tab, bookmark labels, and New Tab links. Surface depth comes from stepped luminance rather than shadows. The complete token system, color tables, and design philosophy are documented in [THEME-SPEC.md](THEME-SPEC.md).

## Scope

A Chromium theme styles the browser frame, toolbar, tab strip, bookmark bar, and New Tab Page colors. It cannot affect:

- Web page content or `brave://` pages
- Context menus, Shields, and settings panels
- Private windows, which use Brave's own styling
