# octosense-org.github.io

[English](README.md) | 简体中文

> **要开发 OctoSense 应用？** 你不需要这个仓库：这里只存放生成后的 OctoSense 网站文件。请按 [OctoSense 组织主页](https://github.com/OctoSense-org)给出的顺序阅读：[OctoScript-App-Design-Flow `AGENTS.md`](https://github.com/OctoSense-org/OctoScript-App-Design-Flow/blob/main/AGENTS.md) → [`flows/README.md`](https://github.com/OctoSense-org/OctoScript-App-Design-Flow/blob/main/flows/README.md) → [`docs/QUICKSTART.md`](https://github.com/OctoSense-org/OctoScript-App-Design-Flow/blob/main/docs/QUICKSTART.md)。

OctoSense 网站已发布的静态文件：**https://octosense.org/**（英文）和 **https://octosense.org/cn/**（中文）。

本仓库只存放生成的产物。源码是 [OctoSense-org/OctoSense-website](https://github.com/OctoSense-org/OctoSense-website)（私有仓库）中的 Astro 项目。请不要在这里手动修改文件：每次发布都会替换本仓库中除 `.git` 之外的全部内容，包括这份 README。

## 发布方式

1. 在源码仓库中运行 `npm run publish:pages`（`scripts/publish-pages.mjs`）：以 `SITE_URL=https://octosense.org` 和 `BASE_PATH=/` 构建网站，把本仓库的 `main` 克隆到临时目录，删除除 `.git` 以外的所有文件，然后复制进 `dist/`、部署工作流（`scripts/pages-deploy.yml` → `.github/workflows/deploy.yml`）以及这两份 README（`scripts/pages-repo/`），最后推送一个名为 `Publish website from <source commit>` 的提交。
2. 每次 push 到 `main` 时，**Publish website** 工作流（`.github/workflows/deploy.yml`）会把仓库内容（不含 README 文件）作为 GitHub Pages 产物上传并部署。Pages 的来源是 **GitHub Actions**；自定义域名 `octosense.org` 在仓库的 Pages 设置中配置，因此没有 `CNAME` 文件。

要修改网站，请修改源码仓库后重新发布。构建、测试和部署细节见源码仓库的 README。

## 内容

- `index.html`、`cn/index.html`：英文和中文首页。
- `apps/<app>/`、`cn/apps/<app>/`：十二个应用的使用手册。
- `experience/{aircon,school,health,reunion}/` 及对应的 `cn/` 路径：可交互的 Makepad/WebAssembly 服务体验。
- `wasm/`：这些体验共用的 WASM 卡片运行时。
- `_astro/`：Astro 生成的带哈希的 CSS、JavaScript 和字体资源。
- `font-licenses/`、`favicon.svg`、`social.png`、`robots.txt`、`sitemap.xml`、`.nojekyll`。
