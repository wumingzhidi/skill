# swe-ai-research-studio

面向 **计算机 / 软件工程 / 人工智能** 方向研究生的一站式科研工作台 Codex Skill。把分散的“找文献、读论文、写论文、画图、复现、管笔记”整合为统一子命令，可单点调用，也可按流水线串联。模型无关，兼容 DeepSeek 与 GPT 系列。

## 功能总览

| 模块 | 子命令 | 能力 |
| --- | --- | --- |
| 文献检索 & 引用 | `/lit-search` `/lit-download` `/bib-auto` `/lit-sort` | 检索 arXiv/会议论文、下载链接、BibTeX、批量整理与综述大纲 |
| 论文阅读 | `/paper-quick` `/paper-deep` `/paper-qa` `/paper-translate` `/paper-code-map` `/paper-reproduce` | 粗读筛选、精读笔记、问答、翻译、代码映射、复现评估 |
| 论文写作 & 修改 | `/paper-outline` `/paper-write` `/paper-polish` `/paper-ai-reduce` `/paper-paraphrase` `/paper-format` `/paper-latex` `/paper-word-helper` | 大纲、草稿、润色、降 AI 痕迹、改写、格式、LaTeX、Word |
| 实验 & 数据集 | `/dataset-find` `/exp-plan` `/exp-analysis` | 数据集检索、实验方案、结果分析 |
| 可视化 & 绘图 | `/fig-prompt` `/mermaid-fig` `/kg-lit` | 绘图 prompt、Mermaid 框图、文献知识图谱 |
| 笔记管理 | `/note-gen` `/note-merge` `/note-review` | 科研笔记、批量合并、组会汇报 |

## 目录结构

```text
swe-ai-research-studio/
├── SKILL.md
├── README.md
├── contract.md
├── safety.md
├── prompts/          # 14 个子命令指令文件
├── templates/        # 6 个静态输出模板
├── scripts/          # 4 个可执行脚本
└── examples/         # 演示工作流
```

## 安装

1. 复制整个 `swe-ai-research-studio/` 文件夹到 Codex 技能目录：
   - Windows：`C:\Users\<你的用户名>\.codex\skills\`
   - macOS/Linux：`~/.codex/skills/`
2. 确保最终路径为 `.../skills/swe-ai-research-studio/SKILL.md`。
3. 在 Codex 中开启自动技能发现，或显式调用 `$swe-ai-research-studio`。

## 使用

- 自然语言触发：`帮我找几篇 LLM agent 的论文并做精读笔记`
- 子命令触发：`/lit-search transformer attention`
- 流水线：`/lit-search → /paper-quick → /paper-deep → /note-gen → /fig-prompt`

## 示例

见 [examples/demo-workflow.md](examples/demo-workflow.md)。

## 脚本

```bash
python scripts/extract_pdf.py paper.pdf --pages 1-10 --out paper.txt
python scripts/arxiv_meta_fetch.py "attention is all you need" --bib
python scripts/bib_cleaner.py refs.bib --out clean.bib
python scripts/export_markdown.py --dir notes/ --out merged.md
```

依赖说明：`extract_pdf.py` 可选 `pypdf`/`PyPDF2`/`pdfplumber`；`arxiv_meta_fetch.py` 仅用标准库；`bib_cleaner.py` 与 `export_markdown.py` 仅用标准库。

## 学术规范声明

本 Skill 的一切输出必须真实、可溯源、可核验。禁止抄袭、伪造数据、伪造实验结果、伪造参考文献、编造消融实验与指标。改写/降 AI 痕迹仅用于优化表达，不改变原意，不得用于造假、抄袭或规避查重。详见 [safety.md](safety.md)。

## 版本

`0.1.0` · 作者 wumingzhidi · 模型无关（适用DeepSeek / GPT 系列等）
