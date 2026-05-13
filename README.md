# Typeset HTML — 中英文混排长文排版模板库

7 个自包含的 HTML 排版模板，覆盖传统书籍到技术文档的不同气质。不依赖任何外部 CSS 库或构建工具。

## Claude Code 集成

任意目录说「输出 HTML」，自动匹配模板并生成排版文件。

### 配置

把下面这段发给 Claude Code：

```markdown
请帮我安装配置 typeset-html 排版模板库：

1. git clone https://github.com/wwq0327/typeset-html.git ~/Projects/typeset-html
2. 在 ~/.claude/CLAUDE.md 末尾添加：

## 排版输出

当用户说「输出 HTML」「排版输出」时：
按照 ~/Projects/typeset-html/CLAUDE.md 的「自动匹配与生成」规则执行。
不用提问，直接分析内容、匹配模板、生成 HTML。

3. 完成后告诉我
```

> 路径不同时替换 `~/Projects/typeset-html`。

## 模板预览

### 缃素 `classic-book`

暖黄纸色、首字下沉、宽边距 — 适合小说、传记、长篇叙事

<table><tr><td><img src="screenshots/classic-book-top.png" alt="开头"></td><td><img src="screenshots/classic-book-mid.png" alt="中间"></td></tr></table>

### 素笺 `song-essay`

宋体通栏、象牙白、低对比 — 适合随笔、读书笔记、讲义

<table><tr><td><img src="screenshots/song-essay-top.png" alt="开头"></td><td><img src="screenshots/song-essay-mid.png" alt="中间"></td></tr></table>

### 青简 `research-report`

青蓝冷调、柱状图、数据表嵌入 — 适合研究报告、白皮书、论文

<table><tr><td><img src="screenshots/research-report-top.png" alt="开头"></td><td><img src="screenshots/research-report-mid.png" alt="中间"></td></tr></table>

### 琥珀 `magazine-feature`

双栏正文、封面大标题、琥珀色强调 — 适合杂志专题、深度报道

<table><tr><td><img src="screenshots/magazine-feature-top.png" alt="开头"></td><td><img src="screenshots/magazine-feature-mid.png" alt="中间"></td></tr></table>

### 赭石 `editorial-feature`

赭色渐变顶栏、粗体标题、通栏正文 — 适合品牌故事、社论

<table><tr><td><img src="screenshots/editorial-feature-top.png" alt="开头"></td><td><img src="screenshots/editorial-feature-mid.png" alt="中间"></td></tr></table>

### 翠微 `modern-manual`

无衬线正文、代码块、callout 提示框 — 适合技术文档、产品手册

<table><tr><td><img src="screenshots/modern-manual-top.png" alt="开头"></td><td><img src="screenshots/modern-manual-mid.png" alt="中间"></td></tr></table>

### 墨韵 `typo-primer`

以示例文章讲解排版知识 — 适合教学材料、风格展示

<table><tr><td><img src="screenshots/typo-primer-top.png" alt="开头"></td><td><img src="screenshots/typo-primer-mid.png" alt="中间"></td></tr></table>

## 手动使用

1. 在 `templates/` 里找到与你内容类型最匹配的模板
2. 下载 `templates/<slug>/template.html`
3. 将文件投给 AI 写作 Agent，说一句「按此模板的样式生成我的内容」

## 设计原则

理论依据：伊达千代 & 内藤孝彦《文字设计的原理》（中信出版社，2011）。以下提炼可直接指导 CSS 排版的关键规则。

### 字号体系（三级）

- **标题**：最大、最显眼，与正文形成明显差异
- **正文**：阅读核心，标准 16px（≈9pt），长者/儿童读者需放大
- **补充说明**：比正文更小（注释、图说、批注），用黑体/无衬线保持小字可读

### 行距与行长

- 正文行距：`line-height: 1.6～1.8`（半个字到一个字的尺寸）
- 行长控制：中文 15～25 字/行（约 35～55mm），超长需分栏
- 行长越长行距也应越宽；字距拉宽时行距同步拉宽
- 标题可收紧行距（甚至"无行距"），形成一体感

### 边界与版心

- 窄边界 → 信息量大，热闹丰富（资讯杂志、邮购册）
- 宽边界 → 信息量少，高雅舒适（精装书、高端品牌）
- 最小边界 5mm，书籍装订侧（订口）需更宽
- 同一作品全页边界保持一致以维持整体性

### 接近律（分组原则）

- 相关内容靠近，不同内容远离 — 用大/中/小三种间距区分关系层次（远/中/近）
- 照片与说明文字必须紧贴放置

### 视觉导向

- 横排视线：左上 → 右下，呈 Z 形；重要元素放在视线自然扫过的位置
- 有意打破 Z 形 → 制造热闹气氛（传单/休闲杂志）

### 字体气质

| 字体 | 气质 | 适用 |
|------|------|------|
| 宋体 / 衬线体 | 传统、正式、信赖、高雅 | 长篇正文 |
| 黑体 / 无衬线体 | 现代、休闲、清晰、理性 | 标题、技术文档 |
| 楷书 / 手写体 | 诚意、古典、亲切 | 特殊场合 |

同一作品保持字体家族统一，用腰线/字号变化区分层级，不混用不同字体。

### 对比四法

1. **字号对比** — 大小差异越大越醒目
2. **重量对比** — 粗体与细体对比，小而粗 > 大而细
3. **字体对比** — 不同字体风格对比（如宋体标题 + 黑体正文）
4. **色彩对比** — 控制明暗/色相对比调节情感强度

### 中英文混排

- 英文词用 `<span class="en">` 包裹，使用衬线斜体保持书卷气
- baseline 对齐：英文与小字号中文对齐基线，与大字号中文对齐 x-height
- 数字和百分比保持等宽感，避免表格视觉摇晃
- 颜色承担分类功能而非装饰功能

### 模板约束

- 每个模板面向特定内容类型，不在同一模板里混用多种风格元素
- 强调点不宜过多，正文以稳定节奏为主，标题和重点处改变节奏

### 生成方式

模板由 Codex（OpenAI GPT-5）生成初稿，人工微调至符合上述原则。调整重点：字体层级、行距行长、配色克制度、装饰元素取舍。

## 技术说明

- 每个模板是独立的 HTML 文件，CSS 全部内嵌
- 无需 Node.js、npm 或任何构建步骤
- 用浏览器直接打开即可预览排版效果
- 自动匹配规则在 `CLAUDE.md`，Agent 操作手册在 `AGENTS.md`
