# Ovateq Docs — v36 GitHub Deployment

## What changed in v36

### Bug fixes
- **Preview flicker fixed** — two separate ResizeObservers now handle available
  space and content height independently, breaking the cascade loop that caused
  the live preview to flicker repeatedly.
- **Qty field now visible** — padding reduced from px-3.5 to px-1.5 so the
  value shows correctly inside the 72px grid column.
- **"Couldn't start" after deploy fixed** — the boot watchdog now calls
  reg.update() on every load, so the new service worker installs and claims
  immediately instead of leaving the old cached chunks in place. Future deploys
  will self-recover without users seeing the error screen.

### New features
- **Collapsible editor panel (desktop)** — ◧ Hide / ◧ Show button beside Save
  collapses the form so the live preview expands to full width. Mobile unchanged.
- **Pro feature locking** — Invoice, Receipt, CV and Application are greyed out
  with lock badges for non-Pro users. Clicking shows a modal directing to Pro
  Activation. Direct URL access is also blocked at the route level.
- **One key, one device enforced** — v2 floating keys rejected for customer tags.
  All customer Pro licences must be v3 (device-bound OVTP3 keys).

## Deploy to GitHub Pages
Replace your gh-pages branch content with the files in this folder.
Ensure your Pages source points to the branch root containing index.html.
