# 图片压缩 · Image Compressor

> 100% 本地处理、隐私优先的纯前端图片压缩工具。图片**不会上传到任何服务器**，断网也能用。
> A 100% in-browser, privacy-first image compressor. Your images **never leave your device**.

---

## ✨ 功能 Features

- 🔒 **隐私优先 / Privacy first** — 全部在浏览器内用 Canvas + Web Worker 压缩，零上传（DevTools Network 无任何请求）。
- 🌐 **中英双语 / Bilingual** — 一键切换中文 / English，所有界面文案（含底部 FAQ）同步切换。
- 📱 **移动端适配 / Mobile-friendly** — 响应式布局，手机上设置栏全宽、列表卡片化、滑块对比支持触摸。
- 🎚️ **质量 / 格式 / 目标大小** — 质量滑块（1–100%）、输出格式（保持原格式 / JPG / PNG / WebP）、目标大小（输入 KB 自动二分调质量）。
- 🔍 **对比预览** — 原图 / 压缩图「并排」与「滑块」两种对比模式，实时显示尺寸与体积。
- 📦 **下载** — 单张下载、ZIP 打包（重名自动加序号）、复制到剪贴板。
- 📴 **离线可用 / PWA** — Service Worker + manifest，断网可打开、可安装到主屏。
- 🔎 **SEO 就绪** — 结构化数据、Open Graph、hreflang、静态可抓取 FAQ、robots.txt、sitemap.xml。

---

## 🧩 技术栈 Tech

纯静态、零运行时依赖、零 CDN：

- 单文件 `index.html`（HTML + CSS + JS，内联 Web Worker）
- `sw.js` — Service Worker（离线缓存）
- `robots.txt` / `sitemap.xml` — 搜索引擎抓取
- 压缩：`canvas.toBlob` 原生编解码 + Web Worker 异步（不支持时降级主线程）

---

## 🚀 本地运行 Run locally

无需安装任何依赖，任选其一：

```bash
# 方式一：Python 自带服务器
python -m http.server 8765
# 浏览器打开 http://127.0.0.1:8765/index.html

# 方式二：Node
npx serve .
```

> 建议用本地服务器而非 `file://` 直接打开，否则 Service Worker / PWA 可能不生效。

---

## ☁️ 部署到 Vercel Deploy to Vercel

本项目是纯静态站点，**无需构建**。

**方式 A：连 GitHub 一键导入（推荐）**
1. 把本仓库推到 GitHub。
2. 打开 [vercel.com/new](https://vercel.com/new) → Import 该仓库 → Deploy。
3. Vercel 会自动识别为静态站点直接发布（也可配合本仓库的 `vercel.json`）。

**方式 B：CLI**
```bash
npx vercel deploy --prod
```
首次会引导登录；之后可用 `VERCEL_TOKEN` 环境变量非交互部署。

部署后请记得把 `index.html` 里的 `robots.txt` / `sitemap.xml` 中的相对路径 `./` 改为你的真实域名。

---

## 📂 目录结构 Structure

```
.
├── index.html              # 主应用（单文件自包含）
├── sw.js                   # Service Worker（离线缓存）
├── robots.txt              # 爬虫规则
├── sitemap.xml             # 站点地图
├── vercel.json             # Vercel 静态部署配置
├── 图片压缩网站_PRD文档.md      # 产品需求文档（PRD）
└── 图片压缩网站_需求文档与方案.md # 需求与技术方案
```

---

## 📝 License

MIT（示例项目，可自由使用与修改）。
