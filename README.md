# slepffxd · 网盘资源分享

夸克网盘资源索引站。**纯静态单文件**：`index.html`（内含全部资源数据）+ 一个 logo，零构建、零依赖、零服务器费用。

- 生产地址：部署后为 `https://<项目名>.pages.dev`
- 数据规模：631 条资源（文件资料 70 / 影视音漫 42 / 教程课程 332 / 游戏资源 171 / 素材杂烩 16）
- 结构：一级大类导航（含「首页」外链）→ 搜索框 → 二级分类 → 资源卡片；每条资源带序号、打开链接，同标题多链接带「备」按钮

## 目录

```
├── index.html                        # 站点首页（单文件，含内嵌 DATA + 样式 + 交互）
├── SLEP FFXD-dt_compressed_.png      # 标题栏 logo
└── README.md
```

## 如何更新内容

页面数据内嵌在 `index.html` 的 `const DATA = ...;` 段。**不要手改这个 HTML**，正确流程：

1. 在 `../../kwke/` 工作区维护权威链接源：`资源/链接分享/*.md`（含失效黑名单 `build/dead_links.txt`）
2. 跑 `kwke/build/rebuild_index.py` 重新生成 `kwke/build/资源索引.html`
3. 覆盖过来：`cp "../../kwke/build/资源索引.html" ./index.html`
4. `git add -A && git commit -m "..." && git push`

推送后 Cloudflare Pages 自动重新部署（约 1 分钟）。

## 部署（Cloudflare Pages）

- 仓库：`slooppools/slepffxd`
- Pages 项目名：`slepffxd`
- Pages 项目：框架预设「无」、构建命令留空、输出目录 `/`
- 无 Functions、无 KV、无环境变量依赖 —— 纯静态，部署即用

本地预览：直接双击 `index.html`，或 `npx serve .`
