# Typeset HTML — 中英文混排长文排版模板库

7 个自包含的 HTML 排版模板，覆盖传统书籍到技术文档的不同气质。不依赖任何外部 CSS 库或构建工具。

## Claude Code 集成（任意目录一键排版）

在**任意项目目录**中说「输出 HTML」，Claude Code 自动分析 Markdown 内容、匹配最佳模板、生成排版文件。

### 安装配置

把下面这段发给 Claude Code，让它自动安装配置：

---

```markdown
请帮我安装配置 typeset-html 排版模板库：

1. 克隆项目到 ~/Projects/typeset-html：
   git clone https://github.com/wwq0327/typeset-html.git ~/Projects/typeset-html

2. 在 ~/.claude/CLAUDE.md 末尾添加以下内容（如文件不存在则创建）：

## 排版输出

当用户说「输出 HTML」「output HTML」「排版输出」「生成 HTML」时：
按照 ~/Projects/typeset-html/CLAUDE.md 的「自动匹配与生成」规则执行。
不用提问，直接分析内容、匹配模板、生成 HTML。

3. 完成后告诉我"配置好了"
```

---

> 如果放到了别的路径，把上面两处 `~/Projects/typeset-html` 换成你的实际路径。

### 使用示例

```bash
cd ~/my-blog
echo "# 一篇技术文章\n\n安装步骤如下…" > draft.md
# 对 Claude Code 说：输出 HTML
# → 自动生成 draft.html（翠微模板）
```

### 匹配逻辑

读取 `index.json`，按内容特征自动选模板：代码块多 → 翠微（技术文档），表格多 → 青简（研究报告），叙事长文 → 缃素（书籍），默认 → 素笺（随笔）。

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

- 每个模板面向特定内容类型，不在同一模板里混用多种风格元素
- 中英文混排时英文使用衬线斜体（`<span class="en">`），与中文段落节奏协调
- 三级字号体系：标题 > 正文 > 补充说明
- 颜色承担分类功能而非装饰功能

## 技术说明

- 每个模板是独立的 HTML 文件，CSS 全部内嵌
- 无需 Node.js、npm 或任何构建步骤
- 用浏览器直接打开即可预览排版效果
- 自动匹配规则在 `CLAUDE.md`，Agent 操作手册在 `AGENTS.md`
