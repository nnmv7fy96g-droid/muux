# Movie Updates Unified — Schedule Site

Auto-generated static site, live at **https://toko.muux.com**.

`index.html` is a nightly copy of `cinema_schedule.html`, produced by the
`cine_scraper` project (a separate, private repo at `~/cine_scraper/` on the
source machine — not connected to this repo's history).

## How it updates
`daily_scrape.sh` in the `cine_scraper` project runs at 3am via launchd:
scrape → TMDB match → generate HTML → copy into this repo → commit → push.
GitHub Pages redeploys automatically on push to `main`.

## Manual redeploy
```bash
cp ~/cine_scraper/cinema_schedule.html ~/cine-schedule-site/index.html
cd ~/cine-schedule-site
git add index.html
git commit -m "Manual schedule update"
git push origin main
```

## Custom domain
`CNAME` file pins this to `toko.muux.com`. DNS is a CNAME record at the
registrar pointing `toko` → `nnmv7fy96g-droid.github.io`.

## Auth
Pushes use a dedicated, per-repo GitHub deploy key
(`~/.ssh/id_ed25519_github_pages` on the source machine), not a personal
account key — see `PRIMER.md` in the `cine_scraper` project for the full
setup notes.
