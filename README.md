# octosense-org.github.io

English | [简体中文](README.zh-CN.md)

> **Building an OctoSense app?** You do not need this repository: it holds the generated OctoSense website only. Start from the [OctoSense organization profile](https://github.com/OctoSense-org)'s reading order: [OctoScript-App-Design-Flow `AGENTS.md`](https://github.com/OctoSense-org/OctoScript-App-Design-Flow/blob/main/AGENTS.md) → [`flows/README.md`](https://github.com/OctoSense-org/OctoScript-App-Design-Flow/blob/main/flows/README.md) → [`docs/QUICKSTART.md`](https://github.com/OctoSense-org/OctoScript-App-Design-Flow/blob/main/docs/QUICKSTART.md).

The published static files for the OctoSense website: **https://octosense.org/** (English) and **https://octosense.org/cn/** (中文).

This repository holds generated output only. The source is the Astro project in [OctoSense-org/OctoSense-website](https://github.com/OctoSense-org/OctoSense-website) (private). Do not edit files here by hand: each publish replaces everything in this repository except `.git`, including this README.

## How it is published

1. In the source repository, `npm run publish:pages` (`scripts/publish-pages.mjs`) builds the site with `SITE_URL=https://octosense.org` and `BASE_PATH=/`, clones this repository's `main` into a temporary directory, removes every file except `.git`, and copies in `dist/`, the deployment workflow (`scripts/pages-deploy.yml` → `.github/workflows/deploy.yml`) and these READMEs (`scripts/pages-repo/`). It then pushes one commit named `Publish website from <source commit>`.
2. On each push to `main`, the **Publish website** workflow (`.github/workflows/deploy.yml`) uploads the repository as the GitHub Pages artifact, leaving out the README files, and deploys it. The Pages source is **GitHub Actions**; the custom domain `octosense.org` is set in the repository's Pages settings, so there is no `CNAME` file.

To change the website, change the source repository and publish again. See its README for build, test and deploy details.

## Contents

- `index.html`, `cn/index.html`: English and Chinese homepages.
- `apps/<app>/`, `cn/apps/<app>/`: the twelve application manuals.
- `experience/{aircon,school,health,reunion}/` and their `cn/` counterparts: the interactive Makepad/WebAssembly service experiences.
- `wasm/`: the shared WASM card runtime used by those experiences.
- `_astro/`: Astro's hashed CSS, JavaScript and font assets.
- `font-licenses/`, `favicon.svg`, `social.png`, `robots.txt`, `sitemap.xml`, `.nojekyll`.
