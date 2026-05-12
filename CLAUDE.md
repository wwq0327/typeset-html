# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

中英文混排长文 HTML 排版模板集。7 个自包含的 HTML 排版模板，覆盖传统书籍到技术文档的不同气质，每个模板内嵌 CSS，不依赖外部库或构建工具。

## 使用方法

1. 下载需要的模板 HTML 文件
2. 将模板文件投给 AI 写作 Agent，告诉它"按此模板的样式生成我的内容"
3. Agent 会保持模板的排版风格，将你的内容填入其中

也可以直接用浏览器打开查看模板的排版效果。选择一个与你内容气质最接近的模板即可。

## 模板一览

| 文件 | 中文名 | 气质 | 适用场景 |
|---|---|---|---|
| `classic-book.html` | **缃素** | 暖黄纸色、首字下沉、宽边距 | 传统书籍阅读 |
| `song-essay.html` | **素笺** | 宋体通栏、象牙白、低对比 | 随笔、讲义、读书笔记 |
| `research-report.html` | **青简** | 青蓝冷调、柱状图、数据表嵌入 | 研究报告、白皮书 |
| `magazine-feature.html` | **琥珀** | 双栏正文、封面大标题、琥珀色强调 | 杂志专题、深度报道 |
| `editorial-feature.html` | **赭石** | 赭色渐变顶栏、粗体标题、通栏正文 | 专题文章、品牌故事 |
| `modern-manual.html` | **翠微** | 无衬线正文、代码块、callout 提示框 | 知识库、产品文档、手册 |
| `typo-primer.html` | **墨韵** | 以示例文章讲解排版知识 | 排版教学参考 |

## 设计原则

- 每个模板面向特定内容类型，不在同一模板里混用多种风格元素
- 中英文混排时英文使用衬线斜体（`<span class="en">`），与中文段落节奏协调
- 三级字号体系：标题 > 正文 > 补充说明
- 颜色承担分类功能而非装饰功能
