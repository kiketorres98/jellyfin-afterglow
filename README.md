# Afterglow for Jellyfin

A calm, cinematic dark theme for the Jellyfin web client. Pure CSS: one file, no plugin, no build step.

| Details page | Library | Home shelves |
|---|---|---|
| ![Details](screenshots/details.jpg) | ![Library](screenshots/library.jpg) | ![Home](screenshots/home-rows.jpg) |

## What it changes

- **Details page**: a tall picture that fades into the page, a big title logo, the facts as quiet outlined chips, round glass buttons with a big red play button.
- **Posters**: rounded corners, a hairline, a soft lift under the pointer, a slim progress bar, and a small green corner for watched titles instead of a round badge.
- **Shelves**: text under the posters on the left, calmer colours, more air between rows, small round scroll arrows.
- **Top bar**: dark and blurred, so the page never shows through the menu text.
- **One accent colour** drives every button, bar and checkbox (Jellyfin 12 colours everything from `--jf-palette-primary-*`; Afterglow sets those from one variable).

## Install

Dashboard → **General** → **Custom CSS code**, paste:

```css
@import url("https://cdn.jsdelivr.net/gh/kiketorres98/jellyfin-afterglow@v12/afterglow.css");
```

Save, then reload the page (Ctrl+F5 if you still see the old look: Jellyfin keeps the CSS in memory).
To remove it, empty the box and save.

> Use the jsDelivr address, not `raw.githubusercontent.com`: GitHub serves raw files as plain text, which browsers refuse to use as a stylesheet.

## Make it yours

Add these lines **after** the `@import`, in the same box:

```css
:root {
  --ag-accent: #3b82f6;   /* buttons, progress bars, checkboxes (default: #cb302d) */
  --ag-played: #1f9d55;   /* corner mark on watched titles */
  --ag-radius: 10px;      /* posters and cards */
}
```

## Compatibility

- Tested with **Jellyfin web 12.3.0**, desktop layout, dark theme, Chrome. The phone layout was looked at only briefly.
- Plays well with the MediaBar and SeerrFin plugins (their own styles are left alone).
- Needs a browser with `color-mix()` and `backdrop-filter` (any Chrome, Edge, Firefox or Safari from 2023 on). Without them the theme still works but loses the lighter/darker accent shades and the blur.

## Notes for contributors

- Selectors follow the web client's own class names (`.card`, `.cardScalable`, `.itemDetailPage`, `.detailRibbon` …). Jellyfin sometimes forces values with `!important` (for example `margin: 0` on the detail buttons or the centred text under posters): the theme works around those on purpose, see the comments in `afterglow.css`.
- The theme is meant to be changed with variables, not by editing the file.

## License

MIT
