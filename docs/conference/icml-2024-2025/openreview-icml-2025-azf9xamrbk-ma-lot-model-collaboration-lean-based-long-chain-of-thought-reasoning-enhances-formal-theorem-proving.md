---
title: "MA-LoT: Model-Collaboration Lean-based Long Chain-of-Thought Reasoning enhances Formal Theorem Proving"
title_zh: MA-LoT：基于模型协作和Lean的长链式思维推理增强形式定理证明
authors: "Ruida WANG, Rui Pan, Yuxin Li, Jipeng Zhang, Yizhen Jia, Shizhe Diao, Renjie Pi, Junjie Hu, Tong Zhang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=AzF9xAMrBK"
tags: ["query:mm-cot"]
score: 4.0
evidence: 长链式思维在形式定理证明中的应用
tldr: 现有定理证明方法使用单一模型难以兼顾整体证明生成和错误修正。本文提出MA-LoT框架，通过LLM与Lean4验证器的结构化交互实现长链式思维，分离自然语言生成和错误分析任务。实验表明，MA-LoT在定理证明基准上取得了更好性能。该方法展示了长链推理在形式数学中的潜力。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-azf9xamrbk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 709, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-azf9xamrbk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1721, \"height\": 1285, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-azf9xamrbk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 784, \"height\": 497, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-azf9xamrbk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1609, \"height\": 881, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-azf9xamrbk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 783, \"height\": 184, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-azf9xamrbk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 791, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-azf9xamrbk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 782, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-azf9xamrbk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 701, \"height\": 315, \"label\": \"Table\"}]"
motivation: 单一模型在定理证明中难以平衡整体生成和错误修正。
method: MA-LoT通过模型协作分离思维链中的生成与验证步骤。
result: 在定理证明任务上提升了证明成功率。
conclusion: 模型协作的长链思维可有效增强定理证明。
---

## Abstract
Solving mathematical problems using computer-verifiable languages like Lean has significantly impacted the mathematical and computer science communities. State-of-the-art methods utilize a single Large Language Model (LLM) to generate complete proof or perform tree search, but they fail to balance these tasks. We propose **MA-LoT**: *Model-CollAboration Lean-based Long Chain-of-Thought*, a comprehensive framework for Lean4 theorem proving to solve this issue. It separates the cognition tasks of general NL for whole-proof generation and error analysis for proof correction using the model-collaboration method. We achieve this by structured interaction of the LLM and Lean4 verifier in Long CoT. To implement the framework, we propose the novel *LoT-Transfer Learning* training-inference pipeline, which enables the Long CoT thinking capability to LLMs without special data annotation. Extensive experiment shows that our framework achieves a **61.07%** accuracy rate on the Lean4 version of the MiniF2F-Test dataset, largely outperforming DeepSeek-V3 (33.61%), single-model tree search (InternLM-Step-Prover, 50.70%), and whole-proof generation (Godel-Prover, 55.33%) baselines. Furthermore, our findings highlight the potential of combining Long CoT with formal verification for a more insightful generation in a broader perspective.

---

## 论文详细总结（自动生成）

## 论文中文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：形式定理证明（如 Lean4）要求严格的逻辑验证，现有方法分为两类：**树搜索方法**（单步迭代，依赖验证器反馈但缺乏高层自然语言规划）和**整体证明生成方法**（一次性生成完整证明，利用 NL 推理但缺少中间反馈）。两种方法各自存在明显短板，且单一模型难以同时平衡 NL 规划与 FL 验证。
- **整体含义**：本文旨在通过**模型协作**（Prover + Corrector）与**长链式思维（Long CoT）** 的结合，将 NL 高层规划与 FL 验证反馈有机整合，从而提升形式定理证明的准确性与推理深度。这一范式不仅适用于 Lean4，也为其他形式化领域提供了可迁移的框架。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：将形式定理证明分解为两个子任务——**整体证明生成**（由 Prover 模型负责，利用 Long CoT 进行 NL 规划与代码编写）和**基于验证器反馈的错误修正**（由 Corrector 模型负责，在 Long CoT 中分析错误消息并重构证明）。两个模型共享同一基座（LoT-Solver），通过结构化交互实现协作。
- **关键技术细节**：
  - **LoT-Transfer Learning (LoT-TL) 训练-推理管道**：使 LLM 获得领域特定的 Long CoT 能力，而无需专门标注的 Long CoT 数据。
    1. **收集领域 SFT 数据**：构建 LoT-ProveData（54,465 条，含 NL 注释的 Lean4 证明）和 LoT-CorrectionData（64,912 条，含错误消息的正确-错误证明对）。
    2. **NL Long CoT 训练**：在通用数学/科学 Long CoT 数据（OpenO1-SFT-Pro）上训练，使模型具备通用 NL Long CoT 推理能力。
    3. **领域对齐（LoT-TL）**：设置系统提示“WITHOUT Long CoT”，在形式定理证明 SFT 数据（LoT-PD）和修正数据（LoT-CD）上训练，但保留 Long CoT 占位符，从而让模型在推理时通过切换系统提示激活 Lean4 Long CoT 能力。
  - **模型协作推理**：
    - **Prover 模型**：使用系统提示“WITH Long CoT”引导模型生成带 NL 规划的完整 Lean4 证明，提交给 Lean4 验证器检查。
    - **Corrector 模型**：接收错误证明与验证器反馈，在 Long CoT 中分析错误原因，重新规划并生成修正后的证明，可多次迭代直至成功或达到最大重试次数。

### 3. 实验设计：数据集、基准与对比方法
- **数据集**：
  - **MiniF2F-Lean4**（Test 和 Valid 各 244 个问题，共 488 个问题），来源包括 MATH 数据集、AMC/AIME/IMO 竞赛题及手工题目。
  - 额外在 **ProofNet** 上进行了小规模验证。
- **基准 (Benchmark)**：以 MiniF2F-Test 的**准确率（pass@k）** 为主要评价指标，同时记录 MiniF2F-Valid 和平均准确率。
- **对比方法**：
  - **树搜索方法**：ReProver、Llemma、Expert Iteration、Lean-STaR、InternLM2.5-StepProver。
  - **整体证明生成方法**：GPT-4-Turbo、DeepSeek-Math、Gemini-1.5、TheoremLlama、DeepSeek-Prover-v1.5-RL、STP-Lean、Godel-Prover、DeepSeek-V3。
  - **本文方法**：以 DeepSeek-Prover-v1.5-SFT 和 Godel-Prover-SFT 为基座，分别使用 LoT (whole-proof) 和 MA-LoT 全框架，以及累积结果（Cumulative）。

### 4. 资源与算力
- **训练开销**：约 **1 GPU 天**（在 4×H100-96G 集群上），主要包括 NL Long CoT 训练（1E-5 学习率）、LoT-TL 在 LoT-PD 上的训练（1E-7 学习率）及在 LoT-CD 上的训练（1E-6 学习率）。
- **评估开销**：约 **11 GPU 天**（同一集群），因为未使用 vLLM 等加速推理，且采样量大（如 pass@128）。
- 文中明确说明了总计算成本。

### 5. 实验数量与充分性
- **主要实验**（表 1）在 MiniF2F 上对比了 10+ 基线，覆盖树搜索和整体生成两类方法。
- **校正器研究**（表 2）：测试多轮校正（Round 1-3）的累积效果，并比较使用 Prover 作为 Corrector 的效果。
- **消融实验**（表 3）：逐步检查训练组件（NL CoT、SFT、Correction Data）以及 Long CoT 开关的影响。
- **效率研究**（表 4）：对比 MA-LoT 与基座模型在相近计算预算下的准确率。
- **缩放定律研究**（Appendix C，图 3）：展示训练步数与性能的对数线性关系（R²=0.9664）。
- **案例研究**（Appendix E）：定性展示 Prover 的规划能力和 Corrector 的错误分析能力。
- **公正性**：采样预算对齐（pass@128 或 pass@32），树搜索方法的搜索成本尽量与整体生成方法一致；排除不可比的基线（如 RMaxTS 的大采样量）。对比方法包括开源与闭源模型，覆盖主流工作。

**总体评价**：实验设计全面，消融充分，对比公平，结果可靠。

### 6. 论文的主要结论与发现
- **性能提升**：MA-LoT 在 MiniF2F-Test 上达到 **61.07%** 准确率，超过所有基线（Godel-Prover 55.33%，InternLM-Step-Prover 50.70%）。即使仅用 whole-proof 生成（LoT），也取得 **57.79%**（Godel-Prover 基座）。
- **模型协作优于单模型**：将计算资源从更多整体生成转移给正确模型（再分配），带来额外 2.46% 的提升（DeepSeek-Prover 基座）。
- **Long CoT 是核心能力**：消融显示切换关闭 Long CoT 导致性能下降（51.64%→49.18%），且 Long CoT 训练相比纯 RL 训练效果更好。
- **缩放律成立**：训练数据越多，性能对数线性提升。
- **校正器有效性**：经过多轮校正，额外解决了约 11.55% 的难题（尤其 IMO/AIME 级别），且专用 Corrector 优于用 Prover 充任的变体。

### 7. 优点：方法或实验设计上的亮点
- **方法创新**：
  - 首创将形式定理证明分解为“规划生成”与“错误修正”两个角色，并通过 Long CoT 融合 NL 与 FL。
  - LoT-TL 管道巧妙地利用系统提示开关实现领域特定 Long CoT 能力涌现，避免昂贵的专门标注。
  - 模型协作框架兼具树搜索的反馈机制与整体生成的高层规划优势。
- **实验亮点**：
  - 消融实验细致验证了每个组件的贡献。
  - 校正器研究揭示了多轮修正的实际收益，并比较不同矫正策略。
  - 缩放律实验表明方法可随数据规模扩展。
  - 案例展示直观证明框架在复杂题目（如 IMO）上的有效性。

### 8. 不足与局限
- **基准规模有限**：仅使用 MiniF2F（488 题），未在更大/更难基准（如 ProofNet、Putnam 等）上全面评估（仅在 Appendix D 对 ProofNet 做了小规模对比，准确率较低）。
- **算力消耗**：特别是评估阶段（11 GPU 天），因无法使用 vLLM 加速，实际部署成本较高。
- **领域特定性**：方法紧密依赖 Lean4 验证器，未展示直接迁移到其他形式系统（如 Isabelle、Coq）的可行性。
- **数据来源局限**：训练数据来自现有数据集和模型生成，可能包含噪声或偏差，且 NL 注释由 Qwen-2.5-72B 自动生成，质量可能不一致。
- **未见偏差/公平性分析**：未讨论模型在特定数学领域（如几何 vs 代数）上的性能差异，也未分析失败案例的模式。
- **校正迭代次数上限**：实验中最多进行 3 轮修正，未探索更多轮次的收益递减点。

（完）
