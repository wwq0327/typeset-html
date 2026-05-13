# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with this repository.

## 自动匹配与生成（外部调用入口）

当用户说「输出 HTML」「output HTML」「排版输出」「生成 HTML」时，执行以下流程。
**不要提问，直接分析、匹配、生成。**

### 1. 定位 Markdown

在当前工作目录找 `*.md` 文件。多个时优先 README.md，其次最近修改的。无 .md 则告知用户。

### 2. 分析内容并匹配模板

读取 `index.json`，按以下特征匹配：

| 检测特征 | 匹配模板 | slug |
|---------|---------|------|
| 代码块 ≥ 3，或含 安装/配置/API/函数/参数/接口/命令行 | **翠微** | `modern-manual` |
| 表格 ≥ 2，或含 摘要/方法论/结果/数据/分析/结论/参考文献 | **青简** | `research-report` |
| 引用 ≥ 3，或含 采访/报道/调查/深度/事件/人物 | **琥珀** | `magazine-feature` |
| 首段 > 500 字 + 叙事特征（章节/人物/场景/情节/故事） | **缃素** | `classic-book` |
| 第一人称多（我/觉得/想起/或许/那天/回忆）+ 短中篇 | **素笺** | `song-essay` |
| 含 品牌/使命/愿景/社论/价值/理念 | **赭石** | `editorial-feature` |
| 大量排版术语（字号/行距/字体/版心/边界/衬线） | **墨韵** | `typo-primer` |
| 以上均不匹配 | **素笺**（默认） | `song-essay` |

多条规则同时命中时，取最先匹配到的。

### 3. 注入内容

读取匹配模板的 `templates/<slug>/template.html`，替换内容：

**替换：**
- 标题 → `<h1>`（含英文副标题用 `.title-en`）
- 副标题/导语 → `.subtitle`、`.lead`、`.dek`（按模板实际类名）
- 作者/日期 → `.meta` 区，保持模板原有格式
- 正文全部 → `<article>` 或 `.content` 容器内，逐段填入
- 代码块 → `<pre><code>`，保留语言标记
- 表格 → `<table>`，保留表头
- 引用 → `<blockquote>`
- 列表 → `<ul>/<ol>`
- 尾注 → `.note`、`.endnote` 区

**绝不动：**
- `<style>` 标签内全部内容
- Google Fonts 链接
- CSS 变量（`--*`）
- 字体声明（`font-family`）
- 配色、背景色
- 装饰元素：首字下沉（`::first-letter`）、分隔线、底色块、角标

**混排处理：**
- 英文词用 `<span class="en">` 包裹（`modern-manual` 除外，它全局无衬线）

### 4. 输出

- 写入当前工作目录
- 文件名：取源 .md 文件名，扩展名改为 `.html`（如 `article.md` → `article.html`）
- 如无法确定文件名，默认 `output.html`
- 输出后告知匹配理由（一句话）

---

## 项目概述

中英文混排长文 HTML 排版模板库。每个模板是自包含的 HTML 文件（内嵌 CSS），覆盖传统书籍到技术文档的不同气质。不依赖外部库或构建工具。

## 模板一览

| 目录 | 中文名 | 气质 | 适合内容 |
|---|---|---|---|
| `classic-book` | **缃素** | 暖黄纸色、首字下沉、宽边距 | 小说、传记、长篇叙事 |
| `song-essay` | **素笺** | 宋体通栏、象牙白、低对比 | 随笔、读书笔记、讲义 |
| `research-report` | **青简** | 青蓝冷调、柱状图、数据表 | 研究报告、白皮书、论文 |
| `magazine-feature` | **琥珀** | 双栏正文、封面大标题 | 杂志专题、深度报道 |
| `editorial-feature` | **赭石** | 赭色渐变顶栏、通栏正文 | 品牌故事、社论 |
| `modern-manual` | **翠微** | 无衬线正文、代码块、callout | 技术文档、产品手册 |
| `typo-primer` | **墨韵** | 排版知识示例文章 | 教学材料、风格展示 |

## 设计原则

- 每个模板面向特定内容类型，不在同一模板里混用多种风格元素
- 中英文混排时英文使用衬线斜体（`<span class="en">`），与中文段落节奏协调
- 三级字号体系：标题 > 正文 > 补充说明
- 颜色承担分类功能而非装饰功能

## 目录结构

```
├── index.json             # 模板元数据索引（Agent 首选入口）
├── AGENTS.md              # Agent 操作手册
├── templates/
│   ├── classic-book/
│   │   ├── template.html  # 模板本体
│   │   └── template.json  # 结构化元数据
│   └── ...（7 个模板）
└── archive/               # 旧版 HTML 文件
```

## 截图方法

使用 gstack browse 工具截取模板预览图，规则如下：

**启动服务**
```bash
python3 -m http.server 8080 &
```

**截图参数**
- 比例：21:9（宽高比 7:3）
- 范围：只截内容主体（`<main>` 或页面主容器），不截背景留白
- 断点：裁剪线落在段落间隙，不切断文字
- 每个模板截两张：开头（顶部区域）和中间（滚动到 h2 附近区域）

**操作步骤**
1. `goto` 模板 URL，`viewport 1200x800`
2. `js` 获取内容容器 bounds 和子元素位置，找到段落边界
3. 顶部截图：`--clip x,firstContentY,w,height`，height 断在干净段落边界，尽量接近 21:9
4. 中部截图：`js window.scrollTo(0, targetY)` 滚动到目标 h2，`--clip x,0,w,height`
5. 每步截图后用 sips 检查尺寸，用图像工具确认无文字截断、无背景露出
6. 输出到 `screenshots/` 目录，命名格式 `{slug}-top.png` / `{slug}-mid.png`
