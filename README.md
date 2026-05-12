# Typeset HTML — 中英文混排长文排版模板库

7 个自包含的 HTML 排版模板，覆盖传统书籍到技术文档的不同气质。下载一个模板，投给 AI 写作 Agent，它就能按模板风格生成你的内容。不依赖任何外部 CSS 库或构建工具。

## 快速使用

1. 在 `templates/` 里找到与你内容类型最匹配的模板
2. 下载 `templates/<slug>/template.html`
3. 将文件投给 AI 写作 Agent，说一句「按此模板的样式生成我的内容」

## 模板预览

### 缃素 `classic-book`

暖黄纸色、首字下沉、宽边距 — 适合小说、传记、长篇叙事

![classic-book 开头](screenshots/classic-book-top.png)

![classic-book 中间](screenshots/classic-book-mid.png)

### 素笺 `song-essay`

宋体通栏、象牙白、低对比 — 适合随笔、读书笔记、讲义

![song-essay 开头](screenshots/song-essay-top.png)

![song-essay 中间](screenshots/song-essay-mid.png)

### 青简 `research-report`

青蓝冷调、柱状图、数据表嵌入 — 适合研究报告、白皮书、论文

![research-report 开头](screenshots/research-report-top.png)

![research-report 中间](screenshots/research-report-mid.png)

### 琥珀 `magazine-feature`

双栏正文、封面大标题、琥珀色强调 — 适合杂志专题、深度报道

![magazine-feature 开头](screenshots/magazine-feature-top.png)

![magazine-feature 中间](screenshots/magazine-feature-mid.png)

### 赭石 `editorial-feature`

赭色渐变顶栏、粗体标题、通栏正文 — 适合品牌故事、社论

![editorial-feature 开头](screenshots/editorial-feature-top.png)

![editorial-feature 中间](screenshots/editorial-feature-mid.png)

### 翠微 `modern-manual`

无衬线正文、代码块、callout 提示框 — 适合技术文档、产品手册

![modern-manual 开头](screenshots/modern-manual-top.png)

![modern-manual 中间](screenshots/modern-manual-mid.png)

### 墨韵 `typo-primer`

以示例文章讲解排版知识 — 适合教学材料、风格展示

![typo-primer 开头](screenshots/typo-primer-top.png)

![typo-primer 中间](screenshots/typo-primer-mid.png)

## 设计原则

- 每个模板面向特定内容类型，不在同一模板里混用多种风格元素
- 中英文混排时英文使用衬线斜体（`<span class="en">`），与中文段落节奏协调
- 三级字号体系：标题 > 正文 > 补充说明
- 颜色承担分类功能而非装饰功能

## Agent 集成

项目提供 `index.json`（结构化元数据索引）和 `AGENTS.md`（Agent 操作手册），方便 AI Agent 按内容类型自动匹配模板。详见 `AGENTS.md`。

## 技术说明

- 每个模板是独立的 HTML 文件，CSS 全部内嵌
- 无需 Node.js、npm 或任何构建步骤
- 用浏览器直接打开即可预览排版效果
