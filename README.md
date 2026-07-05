# Terminal Workbench — Brave Browser Theme

Two Chromium theme extensions that bring the [Terminal Workbench](THEME-SPEC.md) visual system to Brave's chrome: layered green-graphite surfaces, the mint/green accent on the active tab and bookmark-bar text, cyan New Tab Page links, and otherwise quiet UI.

- `dist/terminal-workbench-dark` — graphite dark mode
- `dist/terminal-workbench-light` — the light-mode palette

## Install (Brave)

1. Open `brave://extensions` and switch on **Developer mode** (top right).
2. Click **Load unpacked** and select `dist/terminal-workbench-dark` (or `-light`).

Chromium allows one theme at a time: loading the other folder replaces the current one, and Brave won't auto-switch with the OS — swapping modes is manual. To go back to stock, remove the extension or use *Reset to default* under `brave://settings/appearance`.

> **New Tab Page:** Brave paints its own background image over the NTP by default. To see the theme's NTP colors, open the NTP customize menu and turn off the background image.

## Tweaking the palette

All colors live in `tokens.json` (both modes, spec token names). After editing:

```sh
node build.mjs
```

(Node 18+, no dependencies.) The script regenerates both `dist/` manifests and runs a WCAG contrast gate over every text/surface pair it emits — it refuses to write if a pair drops below its target (4.5:1 for primary text, 3:1 for de-emphasized UI). Then reload the theme from `brave://extensions`.

## What a Chromium theme can't touch

- Web page content, `brave://` pages, context menus, and Brave's Shields/settings panels.
- Private windows (Brave forces its own styling).

The full token system and design philosophy live in [THEME-SPEC.md](THEME-SPEC.md).
