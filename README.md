# purple-shell-interactive.github.io

Website of Purple Shell Interactive: https://purple-shell-interactive.github.io/

Plain static HTML plus one shared `styles.css`. There's no build step. Whatever is on `main` is the live site.

## Rules for every page

- No cookies, analytics, trackers, external scripts or web fonts. The privacy pages depend on this.
- Link the shared stylesheet with `<link rel="stylesheet" href="/styles.css">` and use root-relative links (`/...`) so pages work at any depth, including the 404 page.
- Keep `app-ads.txt` and `.nojekyll` at the root.
- The game-table banner (`.table` in `styles.css`) and the home page hero borrow Solitaire's art from `/solitaire/img/`. If the studio gets its own logo or background, put them in `/img/` and point those two places there.

## Add a new game

1. Copy `solitaire/` to `<game-slug>/` (lowercase with hyphens, e.g. `space-golf/`).
2. Replace the art in `<game-slug>/img/` with the new game's own images: `logo.png`, `background.jpg` (about 1280x720 and under 100 KB), plus any cards or sprites. Then edit `<game-slug>/index.html`: the title, the one-sentence description, the image paths, and the links pointing to `/<game-slug>/privacy/`.
3. Edit `<game-slug>/privacy/index.html`: replace the policy text with the new game's policy. It must match what the app really does and what its Play Console Data safety form declares. Keep `lang="es"` on the Spanish half.
4. In the root `index.html`, copy the Solitaire `<div class="game">` block for the new game, and add its privacy link to the footer.
5. Publish (below). The policy URL for Play Console is `https://purple-shell-interactive.github.io/<game-slug>/privacy/`.

Once a game's privacy URL is in Play Console, don't rename or move it.

## Publish

Commit and push to `main`, with GitHub Desktop or with:

```
git add -A
git commit -m "Describe the change"
git push
```

GitHub Pages redeploys automatically in about a minute. You can watch progress in the repo's **Actions** tab. Settings: **Settings → Pages → Deploy from a branch → main, / (root)**, with **Enforce HTTPS** on.

Check the result:

```
curl -I https://purple-shell-interactive.github.io/<game-slug>/privacy/
```

This must return `HTTP/2 200`.

## app-ads.txt

When Unity LevelPlay is set up, replace the comment in `app-ads.txt` with the lines LevelPlay gives you. The file must stay at the site root.
