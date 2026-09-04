# Ovateq Docs on GitHub Pages — v28

This build is identical to v28 but uses **relative paths** (`./assets/…` instead of
`/assets/…`), so it works whether GitHub serves it from the root of a domain
(`user.github.io`) or from a project sub-folder (`user.github.io/ovateq-docs`).
Verified both ways.

Unlike Netlify, **GitHub Pages adds nothing to your pages** — no injected scripts,
no third-party tags. Your files are served exactly as they are.

## What's in the folder

```
index.html            the app
assets/               code + styles
fonts/inter-var.woff2 Inter, self-hosted (offline)
icons/                app icons
sw.js, workbox-*.js   the offline service worker
manifest.webmanifest  install-to-home-screen
.nojekyll             ← IMPORTANT: tells GitHub not to process the folder
```

`.nojekyll` matters: without it GitHub runs the folder through Jekyll, which
silently drops anything starting with `_`.

## Deploy — no Git needed (website only)

1. Unzip `ovateq-docs-app-dist-v28-github.zip`.
2. On github.com create a **new public repository** (e.g. `ovateq-docs`).
3. In the empty repo choose **Add file → Upload files** and drag in everything
   from inside the extracted `ovateq-docs-app-dist` folder — the files, not the
   folder itself.
4. Commit.
5. **Settings → Pages → Source: Deploy from a branch → branch `main`, folder
   `/ (root)` → Save.**
6. After about a minute your app is at `https://<username>.github.io/<repo>/`.

If the upload page skips the dotfile (`.nojekyll`), add it afterwards with
**Add file → Create new file**, name `.nojekyll`, leave it empty.

## Deploy — with Git (more reliable)

```bash
cd ovateq-docs-app-dist
git init
git add -A
git commit -m "Ovateq Docs v28"
git branch -M main
git remote add origin https://github.com/<username>/<repo>.git
git push -u origin main
```

Then **Settings → Pages → Deploy from a branch → main / root**.

## Moving your data to the new address

A new address is a new database on every device, so:

1. On the **old** site: **More → Backup & Restore → Export** → keep the JSON.
2. On the **new** address: **Backup & Restore → Import** that file.
   Documents, customers, business profile, branding, licence **and the support
   details** all come across.
3. Set up the Owner Console again on the new address (the owner PIN is per-device
   by design — it is deliberately never part of a backup).

## One difference from Netlify

GitHub Pages ignores `_headers`, so the "always revalidate index.html" rule
doesn't apply there — GitHub caches pages for about **10 minutes**. In practice:
after you deploy an update, a device can show the previous build for up to ten
minutes, then the service worker notices, updates and reloads by itself. If
anything ever looks stale, just reload once. Genuine failures still show the
recovery card with Reload / Reset.

## Check it worked

Open the address, then **More → Support** — the bottom line should read
**App build 2026-09-04 00:5x**. That's how you know which build you're on.
