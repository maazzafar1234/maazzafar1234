# 🥷 Setup Guide — Shadow Coder Profile

This file is just for you — it won't show on your GitHub profile. Delete it after setup if you like.

## ⚠️ Fixing broken images (read this first)
If your profile currently shows broken-image icons where the banner/badge/stats should be, it's almost always one thing: **the SVG and PNG files were never actually committed to the repo — only the README text was.** The README references `banner.svg`, `avatar.png`, etc. by filename, so if those files aren't sitting right next to `README.md` in the repo, every image link is pointing at nothing.

Quick check: go to `github.com/maazzafar1234/maazzafar1234` and look at the file list. Do you see `banner.svg`, `banner-light.svg`, `lanyard.svg`, `stats.svg`, `langs.svg`, `trophies.svg`, and `avatar.png` sitting at the root, next to `README.md`? If not, that's the fix — upload them (see Step 2 below), then hard-refresh the page.

Other things that cause this same symptom:
- Uploading the files into a subfolder (e.g. `assets/`) without updating the paths in `README.md` to match
- A typo in a filename (case-sensitive — `Avatar.png` ≠ `avatar.png`)
- Only committing to a branch other than `main`/`master` (the profile page always renders the default branch)

## What's in this package
```
README.md                     → your profile page content
banner.svg / banner-light.svg → animated header (auto dark/light switch)
lanyard.svg                   → swinging ID badge with your real photo
stats.svg / langs.svg         → local stat cards (edit numbers anytime)
trophies.svg                  → 5 shimmering rank tiles
avatar.png                    → your photo, pre-processed into the crimson duotone look
.github/workflows/snake.yml   → daily contribution-snake generator
```

## Steps

1. **Create the special repo.** On GitHub, click **New repository** and name it **exactly** `maazzafar1234` (must match your username exactly — this is GitHub's magic profile-repo trick). Check "Add a README," then create it.
2. **Upload everything.** In the new repo: **Add file → Upload files**, then drag in *all* the files above (keep `README.md` at the root, and keep the `.github/workflows/snake.yml` path intact — GitHub's upload UI preserves folder structure if you drag the whole `.github` folder in, or you can create the file manually and paste its contents). Commit directly to `main`.
3. **Turn on the snake.** Go to the **Actions** tab → enable workflows if prompted → open **Generate Ninja Snake** → **Run workflow**. It'll create an `output` branch with your contribution snake, recolored in crimson, and refresh daily on its own.
4. **Hard refresh** your profile page (Ctrl/Cmd+Shift+R) — GitHub caches SVGs aggressively.

## Keeping stats accurate (no third-party API = no broken images)
Open `stats.svg`, `langs.svg`, and `trophies.svg` in any text/code editor and update the numbers by hand every so often:
- `stats.svg` → look for `EDIT_STATS` comment: stars, repos, followers, commits, PRs
- `langs.svg` → look for `EDIT_LANGS` comment: adjust % and bar width (max width = 400, so `width = %*4`)
- `trophies.svg` → look for `EDIT_TROPHIES` comment: swap labels/ranks as milestones change

## If an SVG ever looks stale after editing
GitHub caches SVGs hard. Bump a harmless dummy query param in `README.md`'s image tags (e.g. add `?v=2` to the `src`) and commit — that busts the cache instantly.

## Want to swap the photo later?
Replace `avatar.png` with any new square-ish photo (ideally 400×400+, clear face, decent lighting) and keep the same filename — the banner and lanyard both reference it by that name, so nothing else needs to change.
