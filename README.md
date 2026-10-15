# statbar-site

Static site for StatBar, published with GitHub Pages at https://statbar.remnantsecurity.com/ (custom domain set by `CNAME`).

This repo holds build output only. Do not edit it by hand.

## Rebuild

The source is the `site/` directory of the statbar repo (Vite, React, Tailwind). The user guide at `/guide/` is generated from `docs/user-guide.md`.

```sh
cd <statbar repo>/site
npm run guide                   # only if docs/user-guide.md changed (needs pandoc)
bash scripts/local-build.sh     # builds on local disk, writes site/dist
rsync -a --delete --exclude .git --exclude CNAME --exclude README.md <statbar repo>/site/dist/ <this repo>/
cd <this repo> && git add -A && git commit -m "Rebuild site" && git push
```

Never build inside the SMB-mounted statbar repo: see the "marketing site" section of its `CLAUDE.md`. Pushing to `main` deploys.
