# Ovateq Docs — v36 GitHub Deployment

## What changed in v36

### Bug fixes
- **Preview flicker fixed** — the live preview panel on the editor screen no
  longer flickers/refreshes repeatedly. The ResizeObserver was observing both
  the container and the sheet in a single callback, causing a cascade loop.
  Now two separate observers handle available-space and content-height
  independently, breaking the cycle.

- **Qty field now visible** — the quantity input in the items table was
  visually clipped because its padding (px-3.5 = 28 px total) consumed most
  of the 72 px column. Reduced to px-1.5. Values now display correctly.

### New features
- **Collapsible editor panel (desktop)** — a ◧ Hide / ◧ Show button sits
  beside Save on desktop. Clicking it collapses the form panel so the live
  preview expands to the full page width. Clicking again restores the split.
  Mobile is unchanged.

- **Pro feature locking** — Invoice, Receipt, CV and Application are now
  locked for non-Pro users:
  - Cards are visibly greyed out with a lock badge and a "Pro" chip
  - Clicking a locked card shows a clear modal directing the user to
    enter their activation key
  - Direct URL access to locked editor routes is also blocked — the app
    redirects to the Pro Activation screen

- **One key, one device — enforced** — v2 floating keys (no device code)
  are now rejected for all customer tags during activation. Only internal
  OWNE/TEST tags may still use v2. All customer Pro licences must be v3
  (device-bound), so the same key cannot activate a second machine.

## Deploy to GitHub Pages

Replace your current gh-pages / docs branch content with the files in this
folder (excluding this DEPLOY.md if preferred). The app is a fully static
PWA — no server required.

Ensure your GitHub Pages source is set to the branch/folder containing
index.html. The _headers file (in public/) handles Content-Security-Policy
for Cloudflare Pages; GitHub Pages ignores it harmlessly.
