# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

The static website for Still Point Games, an indie mobile studio. It is hosted on GitHub Pages from the `main` branch root. It is plain HTML and CSS: there is no build, package manager, JavaScript, linter or tests. To preview it, open the HTML files in a browser or serve the folder with any static file server.

The site exists mainly to meet requirements from the app stores and the ad network for the game **Balloon Archer** (Android package `com.stillpoint.balloonarcher`):

- `index.html` is the studio landing page. Its domain is the "Website" set in Play Console and the AppLovin account.
- `privacy.html` is the Balloon Archer privacy policy. Play Console and the AppLovin MAX consent flow link to it.
- `app-ads.txt` must be served at the domain root, on the same domain set as the Play Console website. Don't move or rename it.
- `.nojekyll` stops GitHub Pages from running Jekyll. Keep it.

## Conventions

- Both pages share `style.css`. Colors are CSS custom properties on `:root`, with a `prefers-color-scheme: dark` override. Add any new color to both blocks.
- `index.html` uses `header.hero`. Secondary pages such as `privacy.html` use `header.slim`, with a link back home.
- The mobile breakpoint is `max-width: 520px`.

## Placeholders still in the files

- `YOURDOMAIN` appears in the `mailto:` links in `index.html` and in `privacy.html` section 9.
- The "Coming soon to Google Play" badge in `index.html` should become the Play Store link at launch. The replacement markup is in an HTML comment next to it.
- `app-ads.txt` holds only comments. The real lines come from the AppLovin dashboard, plus one block per mediation network.

## Privacy policy accuracy

`privacy.html` describes exactly what the game does: local-only storage (best score, sound/music/vibration settings, tutorial-hint flag), ads through AppLovin MAX, and no accounts. It must change whenever the game changes, for example a new SDK (analytics, crash reporting, IAP), a new mediation network or new locally stored data. When you edit it, also update the "Effective date" near the top. Treat it as a template, not legal advice.

`README.md` has the full publishing steps (domain, GitHub Pages, DNS, HTTPS, email forwarding).
