# ea-dojo-assets

Design sources for [EA Dojo](https://ea-dojo.com), kept apart from the app
so they can be edited and re-exported without touching application code.

## Contents

| Path | What it is | Used at |
| --- | --- | --- |
| `social/og-image.html` | Source for the social preview card (1200×630) | — |
| `social/og-image.png` | Exported card shown when an ea-dojo.com link is shared | `public/og-image.png` in Femimiles/howtoenterprisearchitecture |
| `sensei/sensei-mockup.html` | Design mockup of the EA Dojo sensei: four poses and where he appears on the site | — |
| `sensei/poses/*.svg` | The sensei's poses (welcome, teach, think, bow) and head avatars as standalone SVGs | Source for `src/components/Sensei.tsx` (planned) |

## Updating the social preview

1. Edit `social/og-image.html`. It uses the site's fonts (Newsreader,
   IBM Plex Sans, IBM Plex Mono) and colours.
2. Export it at 1200×630:
   `npx playwright screenshot --viewport-size=1200,630 social/og-image.html social/og-image.png`
3. Copy `social/og-image.png` to `public/og-image.png` in the main repo.
4. After deploying, re-scrape the link in the LinkedIn Post Inspector or
   the Facebook Sharing Debugger, since both cache previews.

Keep the numbers on the card (modules, scenarios, industries) in step with
the live site.
