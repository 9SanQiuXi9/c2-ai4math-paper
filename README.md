# From Generation to Verification: A Structured Audit Framework for Reliable AI Mathematical Reasoning

## 项目概述

本项目是 C2 挑战（AI for Mathematics）的提交产物，包含一篇完整的 LaTeX 学术论文及其配套文档。

论文提出了一个**三层审计框架**（Generation → Semantic Reduction → Verification），用于系统性地评估 AI 辅助数学推理的可靠性。框架以 Curry-Howard 对应为理论基础，将自然语言推理映射为可验证的中间表示（IR），并通过形式化方法检验正确性。

## 文件清单

| 文件 | 说明 |
|------|------|
| `paper.tex` | 论文主文件（LaTeX 源码） |
| `references.bib` | 参考文献数据库（16 条引用，全部已验证） |
| `AI日志.md` | AI 协作日志（Day 1 + Day 2 + Day 3） |
| `AAR.md` | 七维复盘（After Action Review） |
| `README.md` | 本文件 |

## 编译方式

### 方式一：Overleaf（推荐）

1. 在 Overleaf 中新建项目
2. 上传 `paper.tex` 和 `references.bib`
3. 编译器选择 **pdfLaTeX**
4. Overleaf 会自动处理 BibTeX 和多遍编译

### 方式二：本地编译

需要安装 TeX Live（或 MiKTeX）。在终端中执行：

```bash
pdflatex paper.tex
bibtex paper
pdflatex paper.tex
pdflatex paper.tex
```

需要连续编译四次（pdflatex → bibtex → pdflatex × 2）以正确解析所有交叉引用。

## 引用验证说明

`references.bib` 中的 16 条引用均经过人工核验：

- **5 篇 Nature 论文**: 通过 DOI 在 Nature 官网验证
- **7 篇 arXiv/会议论文**: 通过 arXiv ID 或会议论文集验证
- **2 篇经典论文**（Z3, Lean）: 通过 Springer / JAR 验证
- **1 篇讲义**: 内部讲义，版本 1.0（2026-04-11）
- **1 本教材**（Sutton & Barto）: 通过 MIT Press 目录验证

所有引用均在论文正文中被引用，无孤立条目。

## 论文结构

1. **Introduction** — 问题背景与贡献概述
2. **Background** — AI4Math 领域综述与可靠性挑战
3. **The Three-Layer Audit Framework** — 框架定义（Generation / Semantic Reduction / Verification）
4. **Case Studies** — 五个代表性系统的案例分析
5. **Cross-System Analysis** — 跨系统模式提取
6. **Reliability Checklist** — 面向实践者的操作清单
7. **Discussion** — 局限性与未来方向
8. **Conclusion** — 总结

## 日期

2026-09-30 ~ 10-01
