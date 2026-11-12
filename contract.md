# contract.md — 全局输出契约

本文件定义 swe-ai-research-studio 所有产物的统一模板、命名规范、格式约束与真实性校验要求。任何子命令输出都必须满足本契约；子命令专属模板与本契约冲突时，以本契约为准。

## 1. 通用原则

1. 默认输出 Markdown；LaTeX、Mermaid、BibTeX、Python 代码分别放入对应语言的代码块或独立文件。
2. 每个文件开头使用标准 YAML frontmatter（便于 Obsidian/Zotero 导入），至少包含：`title`、`type`、`source`、`created`、`status`、`verified`。
3. 所有“来源可核验”的信息必须附链接或 DOI/arXiv 编号；无法核验的必须显式标注【待验证】。
4. 区分“辅助草稿”与“正式成果”：所有写作类产物必须声明“需用户自行核验、补充原创研究、核对引用与实验”。
5. 不得在产物中出现编造的实验数值、引用、结论；分析类产物若缺少真实数据，只输出分析框架并标注“待用户提供数据”。

## 2. 统一 frontmatter 模板

```yaml
---
title: <论文标题/笔记标题>
type: <lit-search|paper-quick|paper-deep|paper-qa|translate|code-map|reproduce|outline|draft|polish|ai-reduce|latex|dataset|exp-plan|exp-analysis|fig|kg|note|merge|review>
source: <arXiv/DOI/URL，或本地文件路径>
created: YYYY-MM-DD
status: <draft|verified|partial>
tags: [<方向>, <会议/期刊>, <方法>]
verified: <true|false|partial>
---
```

## 3. 文件命名规范

| 产物类型 | 命名 | 示例 |
| --- | --- | --- |
| 文献卡片 | `lit-<第一作者>-<年份>-<slug>.md` | `lit-vaswani-2017-attention.md` |
| 精读笔记 | `notes-<short-title>.md` | `notes-gpt4-eval.md` |
| 综述/排序 | `survey-<topic>-<date>.md` | `survey-llm-agent-2026-11-12.md` |
| 写作草稿 | `draft-<section>.md` | `draft-related-work.md` |
| LaTeX 片段 | `<section>.tex` | `method.tex` |
| BibTeX | `refs-<topic>.bib` | `refs-llm-agent.bib` |
| 实验方案 | `exp-<topic>-plan.md` | `exp-federated-plan.md` |
| 图表代码 | `fig-<name>.mmd / .tikz / .drawio` | `fig-arch.mmd` |
| 知识图谱 | `kg-<topic>.md` | `kg-llm-agent.md` |
| 汇报材料 | `meeting-<date>-<topic>.md` | `meeting-2026-11-12-agent.md` |

## 4. 分块规范

长文本分块时，每块产物头部写明：

```markdown
<!-- chunk: 2/5 | range: 第3章 方法 1-3节 | source: 论文标题 -->
```

合并前保留 chunk 标记，直至 `/note-merge` 或导出脚本完成合并。

## 5. 真实性校验清单（每个产物末尾自查）

- [ ] 引用文献的标题、作者、年份、期刊/会议、DOI/arXiv 是否与来源一致？
- [ ] 实验数据是否来自真实论文/复现结果/用户提供，而非凭空生成？
- [ ] 是否存在把他人结论改写为原创的表述？
- [ ] 无法核验的内容是否已标注【待验证】？
- [ ] 写作类产物是否已附“请自行核验”声明？

## 6. 模板引用

各子命令的详细输出模板在 `prompts/*.md` 中定义；静态模板文件位于 `templates/`：

- 精读笔记 → `templates/paper-notes.md.template`
- 文献卡片 → `templates/lit-card.md.template`
- 复现清单 → `templates/reproduce-checklist.md.template`
- BibTeX → `templates/bib-standard.bib.template`
- LaTeX 片段 → `templates/latex-section.tex.template`
- 汇报提纲 → `templates/meeting-slide-outline.md.template`
