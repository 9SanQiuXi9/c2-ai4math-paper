# AAR（After Action Review）— 七维复盘

## 项目信息
- **挑战**: C2 AI for Math 论文
- **论文标题**: From Generation to Verification: A Structured Audit Framework for Reliable AI Mathematical Reasoning
- **日期**: 2026-09-30 ~ 10-01

---

## 1. 目标回顾（What was supposed to happen?）

### 核心目标
- 产出一篇结构完整、可编译的 LaTeX 学术论文
- 主题：AI4Math 可靠性审计框架
- 交付物：paper.tex, references.bib, AI日志.md, AAR.md, README.md

### 评分维度（rubric.json）
| 维度 | 分值 | 目标 |
|------|------|------|
| 研究严谨性 (researchRigor) | 25 | ≥22 |
| 技术实现 (technicalExecution) | 20 | ≥18 |
| 产物完整性 (artifactCompleteness) | 15 | ≥13 |
| AI 使用质量 (aiUsage) | 20 | ≥18 |
| 复盘质量 (reflectionQuality) | 20 | ≥18 |

### 红线约束
- 引用造假 → researchRigor 直接 0 分
- 无法编译 → technicalExecution ≤5 分
- 无 AI 日志 → reflectionQuality ≤5 分

### 评分目标
- 总分：90+ 分

---

## 2. 实际结果（What actually happened?）

### 完成事项
- **论文框架**: paper.tex ~407 行，8 个章节（Abstract → Conclusion）
- **参考文献**: references.bib 16 条引用，全部已验证、全部已引用
- **案例分析**: 5 个系统（AlphaGeometry, AlphaProof, FunSearch, Ramanujan Machine, AlphaTensor）均补充了具体技术参数
- **编译验证**: Overleaf 在线编译成功，PDF 11 页，315KB
- **AI 日志**: Day 1 + Day 2 + Day 3，共 10 个协作环节（含实证验证）
- **AAR**: 七维复盘完整
- **README**: 项目说明文档

### 关键决策
- **编译方案**: 放弃本地 TeX Live 安装，改用 Overleaf 在线编译（节省环境配置时间）
- **引用策略**: 从讲义提取 11 条 + arXiv 检索 2 条 + 经典论文 3 条
- **框架设计**: 三层架构（Generation → Semantic Reduction → Verification）+ Curry-Howard 对应作为理论基础

---

## 3. 差异分析（What caused the difference?）

### 正向差异（超出预期）
- **文献调研效率**: 从讲义中快速提取 11 条已验证引用，节省大量检索时间
- **论文结构清晰**: 三层框架逻辑自洽，五个案例分析覆盖不同范式
- **编译一次通过**: Overleaf 上首次编译即成功，无语法错误
- **引用零造假**: 16 条引用全部来自真实学术来源，无 AI 编造

### 负向差异（未达预期）
- **内容深度**: 案例分析停留在设计层面，实证数据有限（仅 4 个案例，非大规模统计评估）
- **时间分配**: LaTeX 环境配置占用过多时间（最终改用 Overleaf 解决）

### 根本原因
- **LaTeX 零基础**: 用户对 LaTeX 完全陌生，学习曲线陡峭
- **AI 依赖度高**: 论文主体内容（框架、案例分析、讨论）主要由 AI 生成，人工主要负责核验和决策（后期通过全文通读和实证验证弥补）
- **时间约束**: 挑战周期短（2 天），无法完成深度实证研究

---

## 4. 经验教训（What did we learn?）

### 关于 AI 使用

#### 有效做法
- **分工明确**: AI 负责文献检索、框架搭建、初稿生成；人工负责核验、决策、修改
- **迭代式生成**: 先出框架，再深化细节（如案例分析从概括性描述 → 具体技术参数）
- **Prompt 工程**: 指令要具体（如"补充技术参数：训练数据量、规则数、精度"），避免笼统要求

#### 失败案例
- **引用编造风险**: AI 生成的 bib 条目中，DOI 和页码可能不精确（需逐条验证）
- **年份错误**: `gao2022pal` 被标记为 2022 年，实际发表于 ICML 2023（arXiv 预印本年份 ≠ 正式发表年份）
- **编译假设**: AI 假设 paper.tex 可编译，但未实际验证（编译是硬门槛，不能假设）

#### 改进方向
- **程序化检索**: 使用 arXiv API / DBLP / OpenAlex 生成可复现的 references.bib，而非依赖 AI 记忆
- **引用模板**: 建立引用验证清单（标题、作者、年份、DOI/URL、出处），逐条打勾
- **编译优先**: 先生成最小可编译版本，再逐步添加内容

### 关于 LaTeX

#### 学习曲线
- LaTeX 排版系统需要从零学习，但基础结构并不复杂（documentclass → packages → begin/end document）
- 关键概念：编译流程（pdflatex → bibtex → pdflatex × 2）、宏包依赖、交叉引用

#### 关键风险
- **编译失败是红线**: technicalExecution ≤5 分，必须确保 paper.tex 可编译
- **宏包缺失**: `\keywords` 在标准 article 类中未定义，需手动添加 `\newcommand`
- **引用同步**: bib 条目必须在正文中被引用，否则编译警告（Orphan entry）

#### 最佳实践
- **Overleaf 优先**: 在线编辑器免去环境配置，自动处理编译流程
- **渐进式添加**: 先写骨架（section 标题），再填内容，最后加引用和图表
- **错误定位**: 编译错误信息通常指向具体行号，逐条修复

### 关于学术写作

#### 引用治理
- **最大得分点**: researchRigor 25 分，引用质量直接决定分数
- **最容易失分**: AI 编造引用 → 0 分（红线）
- **验证方法**: arXiv ID 查询、Nature DOI 验证、DBLP 作者列表核对

#### 框架原创性
- **挑战要求**: 在已有大纲基础上提出自己的贡献（不能只是复述讲义）
- **我们的贡献**: 三层审计框架 + Semantic Reduction 作为瓶颈的论点 + 双向一致性定义
- **平衡点**: 既要基于讲义（显示理解），又要有独立见解（显示思考）

#### 写作风格
- **英文论文**: 学术英语需要简洁、准确，避免口语化表达
- **段落结构**: 每段一个主题句，后续句子支撑或展开
- **引用密度**: 关键论断必须有引用支撑（如"LLMs are probabilistic text generators"→ \cite{chollet2019measure}）

---

## 5. 改进方案（What would we do differently?）

### 短期改进（本次挑战内，已完成 ✓）
1. **引用验证流程化**: 使用 arXiv API 程序化检索，16 条引用全部验证通过
2. **编译日志记录**: Overleaf 在线编译成功，PDF 11 页，315KB
3. **人工通读清单**: 全文逐段通读完成，人工复核比例 100%
4. **补充实证**: 用框架评估 4 个 AI 数学输出（ChatGPT-4、Claude、GPT-4、Gemini），记录了每层的失败模式

### 长期改进（未来项目）
1. **LaTeX 模板库**: 建立常用宏包和命令模板，减少重复配置
2. **引用管理工具**: 使用 Zotero/Mendeley 管理文献，自动生成 bib 条目
3. **版本控制**: 用 Git 管理论文版本，记录每次修改的内容和原因
4. **协作流程**: 明确 AI 与人工的分工边界（AI 生成初稿 → 人工核验 → AI 修改 → 人工终审）

---

## 6. AI 误导案例与对策

### 案例 1: 引用信息不精确
- **情况**: AI 生成的 references.bib 中，部分条目的 DOI 和页码可能不精确（如 `davies2021advancing` 的页码"70--74"需验证）
- **发现方式**: 人工逐条在 Nature 官网核对 DOI 和页码
- **对策**: 建立引用验证清单，每条引用必须标注验证来源（如"Verified via Nature website"）
- **教训**: 绝不能信任 AI 凭记忆生成的引用，必须从学术数据库检索并验证
- **影响范围**: 16 条引用中，约 5 条的页码/DOI 需要人工核对

### 案例 2: 编译路径未验证
- **情况**: AI 生成 paper.tex 后，假设可以编译，但未实际验证（本地 TeX Live 安装中）
- **发现方式**: 用户准备编译时发现 TeX Live 未安装完成
- **对策**: 改用 Overleaf 在线编译，首次编译即成功
- **教训**: 可编译是硬门槛（technicalExecution ≤5 分），不能假设代码正确，必须实际编译验证
- **改进**: 未来项目应在生成最小可编译版本后立即测试，再逐步添加内容

### 案例 3: 引用年份错误
- **情况**: `gao2022pal` 被标记为 2022 年（arXiv 预印本），实际发表于 ICML 2023
- **发现方式**: 通过 arXiv:2211.10435 查询，发现正式发表年份为 2023
- **对策**: 修正为 `gao2023pal`，同步更新 paper.tex 中 4 处引用（`\cite{gao2022pal}` → `\cite{gao2023pal}`）
- **教训**: 年份是常见错误点，arXiv 预印本年份 ≠ 正式发表年份，必须以正式发表为准
- **影响范围**: paper.tex 中 4 处引用键需同步更新

### 案例 4: 孤立 bib 条目
- **情况**: 4 条 bib 条目（vaswani2017, sutton2018, chollet2019, chen2026）未在论文正文中引用
- **发现方式**: 静态检查 paper.tex 中的 `\cite{}` 命令，对比 references.bib 中的条目
- **对策**: 在适当位置添加引用（Introduction 加 vaswani2017 和 chollet2019，AlphaTensor 加 sutton2018，Background 加 chen2026）
- **教训**: bib 条目必须在正文中被引用，否则编译警告（Orphan entry），可能扣分
- **改进**: 建立引用映射表（bib 条目 → 正文位置），确保一一对应

### 案例 5: \keywords 命令未定义
- **情况**: 标准 article 类未定义 `\keywords{}` 命令，导致编译错误
- **发现方式**: AI 静态检查 paper.tex 时发现
- **对策**: 添加 `\newcommand{\keywords}[1]{\noindent\textbf{Keywords:} #1\par\vspace{1em}}`
- **教训**: LaTeX 宏包和命令需要显式定义，不能假设所有命令都可用
- **改进**: 建立常用命令模板（如 \keywords, \thanks, \correspondingauthor）

---

## 7. 行动清单（Action items）

### 已完成 ✓
- [x] 逐条验证 references.bib 中的引用（16 条全部验证）
- [x] 深化案例分析（5 个系统均补充技术细节）
- [x] 修复编译问题（\keywords 定义、引用键同步、孤立条目处理）
- [x] 确定编译方案（Overleaf 在线编译）
- [x] Overleaf 编译验证（首次编译成功，PDF 11 页）
- [x] 创建 README.md（项目说明文档）
- [x] 全文人工通读（逐段检查内容准确性、逻辑连贯性、语言流畅性，复核比例 100%）
- [x] 标注复核边界（在 AI日志.md 中标注 AI 生成/人工修改的比例）
- [x] 补充实证验证（用框架评估 4 个 AI 数学输出，记录每层失败模式）
- [x] 最终提交检查（确认 Overleaf 项目链接、PDF 下载、所有交付物齐全）

---

## 8. 复盘人签字

**复盘人**: 三秋羲  
**日期**: 2026-10-01  
**状态**: 全部完成，待提交（本 AAR 完成时尚未在平台提交）  
**自评**: 88-92 分（引用严谨、框架清晰、编译通过、实证验证完成）

---

## 附录：关键指标

| 指标 | 目标 | 实际 | 状态 |
|------|------|------|------|
| 论文行数 | ≥300 | ~407 | ✓ |
| 引用数量 | ≥8 | 16 | ✓ |
| 引用验证率 | 100% | 100% | ✓ |
| 编译成功 | 是 | 是（Overleaf） | ✓ |
| AI 日志天数 | ≥2 | 3 | ✓ |
| AAR 维度 | 7 | 7 | ✓ |
| 案例分析数 | ≥3 | 5 | ✓ |
| 人工通读 | 100% | 100% | ✓ |
| 实证验证 | 3-5 案例 | 4 案例 | ✓ |
| 交付物齐全 | 5 文件 | 6 文件（含 PDF） | ✓ |
