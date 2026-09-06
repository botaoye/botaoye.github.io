# OmniPoint — project page source

Source for the *OmniPoint: Universal Monocular Metric Pointcloud from Any Camera*
(ECCV 2026) project page.

**Live:** <https://botaoye.github.io/omnipoint/>

## Layout

```
index.html                 the whole page
static/css/                bulma.min.css + fontawesome + index.css, copied from
                           botaoye.github.io/yonosplat/static (same look as the
                           NoPoSplat and YoNoSplat pages)
static/css/omnipoint.css   this page's overrides: navy #24384F / teal #0F7A8A,
                           matching the ECCV poster
static/js/                 fontawesome only — the page has no carousel or navbar
assets/                    web-sized figures, favicon, paper + poster PDFs
make_web_assets.py         regenerates assets/ from the paper and poster sources
deploy.sh                  publishes to GitHub Pages
```

## Rebuilding and publishing

```bash
python make_web_assets.py    # figures <- ../poster_claude/assets, PDFs <- paper + poster
./deploy.sh                  # -> https://botaoye.github.io/omnipoint/
./deploy.sh omnipoint3d      # -> https://omnipoint3d.github.io/  (once the org exists)
```

`deploy.sh` clones the target repo, replaces the page, commits and pushes, then
polls until GitHub Pages serves it. It sets `GIT_SSH_COMMAND=/usr/bin/ssh`
because the interactive shell's `ssh` is shadowed by a wrapper that git cannot
use.

## Notes

- Figures come from `../poster_claude/assets` (already rendered from the
  camera-ready PDFs at ~5000 px and whitespace-trimmed), downscaled to 1800–2000 px
  and re-encoded as progressive JPEG. Total page weight is ~1.4 MB of images
  plus the two PDFs.
- Every number in the three results tables and the abstract were checked
  programmatically against `../ECCV26_OmniPoint_camera_ready/main.tex`
  (Tabs. 1, 2, 3).
- Equations are MathJax; the ray-vs-planar-depth figure is hand-written inline
  SVG, so it stays sharp and themes with the page.
- `https://omnipoint.github.io/` — the URL printed in the camera-ready — is **not
  obtainable**: `omnipoint` is a dormant personal GitHub account from 2010, and
  GitHub only releases usernames for trademark disputes.
