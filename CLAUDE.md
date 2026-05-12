# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with this repository.

## 项目概述

中英文混排长文 HTML 排版模板库。每个模板是自包含的 HTML 文件（内嵌 CSS），覆盖传统书籍到技术文档的不同气质。不依赖外部库或构建工具。

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

## 使用方法

1. 读 `index.json` 按内容类型匹配最合适的模板
2. 用 `templates/<slug>/template.html` 作为基础，替换内容
3. 保留字体、配色、布局、装饰等视觉身份
4. 生成完成后用浏览器打开验证排版效果

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
