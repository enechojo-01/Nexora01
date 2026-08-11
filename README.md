# Nexora Digital

A single-page marketing site for a digital design agency — cinematic scroll-driven hero, services grid, project showcase, animated stats, and a contact form.

**Live site:** https://nexora-digital-ten-ochre.vercel.app

## Stack

- Static HTML, CSS, and vanilla JavaScript — no build step, no framework
- Google Fonts (Inter, Space Grotesk)
- Deployed on Vercel

## Features

- Scroll-pinned "cinematic" hero on desktop: a browser mockup morphs into a dashboard as 3D-transformed layers separate and reassemble while the user scrolls
- Scroll-triggered reveal animations (`IntersectionObserver`) and an animated stat counter
- Accessible mobile navigation (slide-out menu, focus states, skip link)
- Client-side form validation with a `mailto:` fallback (no backend)
- Fully responsive, including a simplified static hero on mobile (see below)

## Project background

The initial build was AI-generated, then debugged and refined by hand — most notably the mobile responsive pass described below.

### Mobile fix

The desktop hero uses a pinned/scroll-hijacked section: text is absolutely centered over a 3D mockup that's driven by scroll position. That centering trick assumed a two-column layout. On mobile, the layout collapses to a single column and the text container's height collapses to `0`, which broke the vertical centering math and pushed the headline off the top of the viewport — visible as an overflowing, half-cut-off hero on any phone-sized screen.

Fix: mobile (`≤768px`) now gets a simplified, static hero — normal document flow, no pinning, no absolute centering, decorative 3D mockup hidden. The scroll-driven JavaScript now checks the same viewport width and skips its calculations on mobile instead of fighting the CSS. A leftover block of dead CSS (targeting class names that no longer existed in the markup) was also removed after it was found silently overriding the fix.

## Running locally

No build tools required — it's a single HTML file.

```bash
# clone, then just open it
open index.html

# or serve it locally
npx serve .
```

## Deploying

Deployed as a static site on [Vercel](https://vercel.com) — no configuration needed, it will detect and serve `index.html` directly.

## License

MIT — see [LICENSE](./LICENSE).
