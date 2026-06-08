---
title: "DreamPRM: Domain-reweighted Process Reward Model for Multimodal Reasoning"
title_zh: DreamPRM：面向多模态推理的领域重加过程奖励模型
authors: "Qi Cao, Ruiyi Wang, Ruiyi Zhang, Sai Ashish Somayajula, Pengtao Xie"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ZyiBk1ZinG"
tags: ["query:mm-cot"]
score: 8.0
evidence: 面向多模态逐步推理的过程奖励模型
tldr: 多模态逐步推理中过程奖励模型面临训练分布偏移和数据不足的挑战。提出DreamPRM，通过领域重加权的过程奖励模型，结合多任务学习缓解泛化困难，在多个多模态推理基准上提升了推理步骤评估的准确性，为多模态逐步推理的精细化监督提供了有效方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyibk1zing/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 737, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyibk1zing/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1434, \"height\": 520, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyibk1zing/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1457, \"height\": 563, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyibk1zing/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1450, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyibk1zing/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1444, \"height\": 552, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyibk1zing/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1440, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyibk1zing/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1479, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyibk1zing/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1426, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyibk1zing/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1443, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyibk1zing/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 520, \"height\": 375, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyibk1zing/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 908, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyibk1zing/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1356, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyibk1zing/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1105, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyibk1zing/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1440, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyibk1zing/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 589, \"height\": 321, \"label\": \"Table\"}]"
motivation: 多模态推理的分布偏移导致过程奖励模型泛化困难。
method: 提出领域重加权的过程奖励模型，利用多任务学习扩大覆盖。
result: 在多个多模态推理数据集上显著优于现有PRM。
conclusion: DreamPRM有效提升了多模态逐步推理的评估质量。
---

## Abstract
Reasoning has substantially improved the performance of large language models (LLMs) on complicated tasks. Central to the current reasoning studies, Process Reward Models (PRMs) offer a fine-grained evaluation of intermediate reasoning steps and guide the reasoning process. However, extending PRMs to multimodal large language models (MLLMs) introduces challenges. Since multimodal reasoning covers a wider range of tasks compared to text-only scenarios, the resulting distribution shift from the training to testing sets is more severe, leading to greater generalization difficulty. Training a reliable multimodal PRM, therefore, demands large and diverse datasets to ensure sufficient coverage. However, current multimodal reasoning datasets suffer from a marked quality imbalance, which degrades PRM performance and highlights the need for an effective data selection strategy. To address the issues, we introduce DreamPRM, a domain-reweighted training framework for multimodal PRMs which employs bi-level optimization. In the lower-level optimization, DreamPRM performs fine-tuning on multiple datasets with domain weights, allowing the PRM to prioritize high-quality reasoning signals and alleviating the impact of dataset quality imbalance. In the upper-level optimization, the PRM is evaluated on a separate meta-learning dataset; this feedback updates the domain weights through an aggregation loss function, thereby improving the generalization capability of trained PRM. Extensive experiments on multiple multimodal reasoning benchmarks covering both mathematical and general reasoning show that test-time scaling with DreamPRM consistently improves the performance of state-of-the-art MLLMs. Further comparisons reveal that DreamPRM's domain-reweighting strategy surpasses other data selection methods and yields higher accuracy gains than existing test-time scaling approaches. Notably, DreamPRM achieves a top-1 accuracy of 85.2% on the MathVista leaderboard using the o4-mini model, demonstrating strong generalization capability in complex multimodal reasoning tasks.

---

## 论文详细总结（自动生成）

# DreamPRM: 面向多模态推理的领域重加权过程奖励模型 — 中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：过程奖励模型（PRM）在纯文本大语言模型的逐步推理中取得了成功，通过为每一步推理提供细粒度评分来引导推理过程。  
- **核心问题**：将 PRM 扩展到多模态大语言模型（MLLM）面临两大挑战：  
  - **更严重的分布偏移**：多模态推理的输入空间（图像+文本）比纯文本更广阔且高维，导致训练集到测试集的分布偏移更加剧烈，PRM 的泛化能力大幅下降。  
  - **数据集质量不平衡**：现有的多模态推理数据集普遍存在噪声（如不必要的模态、难度过低的问题），低质量样本会稀释训练信号，降低 PRM 的性能。  
- **整体含义**：为训练可靠的多模态 PRM，需要一种能自动区分高质量与低质量数据的有效方法，以缓解数据集质量差异带来的负面影响，提高 PRM 在多模态推理任务上的泛化能力。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：提出 DreamPRM，一个基于**双层次优化（Bi-level Optimization, BLO）**的领域重加权训练框架。它为每个训练领域（数据集）动态学习一个权重，高质量领域获得更大贡献，低质量领域被抑制，从而自动修正数据质量不平衡。  
- **关键技术细节**：  
  - **数据划分**：将 K 个领域的数据作为训练池 \(D_{tr}\)，另有一个更高质量的元数据集 \(D_{meta}\)（文中使用 MMMU）用于上层优化。  
  - **下层优化（Domain‑Reweighted PRM Training）**：  
    - PRM 参数 \(\phi\) 在多个训练域上以加权和方式优化：  
      \[
      L_{tr}(D_{tr}, \phi, \alpha) = \sum_{k=1}^K \alpha_k L_{tr}(D_k, \phi)
      \]  
      其中 \(\alpha_k\) 是可学习的领域权重，\(L_{tr}(D_k, \phi)\) 是每个领域上的 MSE 损失（预测的逐步概率与蒙特卡洛估计的信号之间的误差）。  
    - 蒙特卡洛信号 \(p_i\)：对于每个部分推理步骤，从 MLLM 多次采样完整回答，利用正确比例作为监督信号。  
  - **上层优化（Learning Domain Weights）**：  
    - 给定下层优化得到的 PRM 参数 \(\phi^*(\alpha)\)，在元数据集上定义**聚合函数损失**：  
      \[
      L_{meta}(D_{meta}, \phi^*(\alpha)) = \sum_{(x,y)} \text{MSE}\left( \sigma(A(V_{\phi^*}(x,\hat{y}))), r(\hat{y}, y) \right)
      \]  
      其中 \(A\) 是聚合函数（对每步 logits 求和），\(\sigma\) 是 sigmoid，\(r\) 是生成结果是否正确的二值信号。  
      - 通过最小化该损失来更新领域权重 \(\alpha\)，使优化目标更接近实际推理时的选择目标。  
  - **优化流程**：采用高效的一步或几步展开（unrolling）近似求解 BLO，交替更新 \(\phi\) 和 \(\alpha\) 直至收敛。

## 3. 实验设计：数据集、基准、对比方法

- **训练数据集**：15 个多模态数据集，涵盖四大类：  
  - **科学**：AI2D, ScienceQA, M3CoT  
  - **图表**：ChartQA, DVQA, MapQA, FigureQA  
  - **几何**：Geo170k, Geometry3K, UniGeo, GeomVerse, GeoS  
  - **常识**：IconQA, InfographicsVQA, CLEVR‑Math  
  每个领域约 1k 样本，共约 15k。  
- **元数据集**：MMMU（约 1k 验证样本）。  
- **测试基准**（5 个）：  
  - **数学推理**：WeMath, MathVista (testmini), MathVision (test)  
  - **通用推理**：MMVet (v1), MMStar (test)  
- **对比方法**（三组）：  
  1. **零样本 SOTA MLLM**：Gemini‑1.5‑Pro, GPT‑4v, LLaVA‑OneVision‑7B, Qwen2‑VL‑7B, InternVL‑2.5‑8B‑MPO  
  2. **其他测试时缩放方法**（基于 InternVL‑2.5‑8B‑MPO）：Self‑consistency, Self‑correction, ORM  
  3. **其他 PRM 方法**：Vanilla PRM（无数据选择），s1‑PRM（基于难度、质量、多样性），CaR‑PRM（基于聚类与排序）  
- **额外评估**：在 MathVista 排行榜上与 VL‑Rethinker、Step R1‑V‑Mini、Kimi‑k1.6、Doubao‑pro‑1.5、Ovis2‑34B、o1、Llama 4 Maverick、Vision‑R1‑7B 等对比。

## 4. 资源与算力

- **硬件**：1 张 **NVIDIA A100 GPU**。  
- **训练时长**：约 **10 小时**，共 **10000 次迭代**。  
- **优化器**：  
  - 下层（PRM）：AdamW，lr=5×10⁻⁷，每外循环 5 步内梯度更新（unroll steps=5）。  
  - 上层（领域权重）：AdamW，lr=0.01，weight decay=1e-3；StepLR 调度器（step size=5000，γ=0.5）。  
- **框架**：使用 Betty 库实现多级优化。  
- 论文声明将公开代码和模型权重。

## 5. 实验数量与充分性

- **主要实验结果**：表 1 报告了 DreamPRM 在 5 个基准上的准确率，对比了 10+ 种方法；DreamPRM 在所有基准上均取得最高或第二高分数。  
- **消融实验**（图 5(c)、表 4）：验证三个关键组件——聚合函数损失、双层次优化结构、结构化思维提示——的重要性，每项移除都导致性能下降 1%~4%。  
- **领域权重分析**（图 7）：展示了 15 个领域学习到的权重（0.55~1.49），发现难度大、需要真正多模态推理的领域（如 M3CoT, FigureQA）获得高权重，简单领域（如 AI2D）权重低，验证了重加权策略的有效性。  
- **缩放能力与泛化**（图 6、表 3）：  
  - 在 5 个基准上，从 k=2 到 k=8 个 CoT 候选，DreamPRM 准确率持续提升。  
  - 将 DreamPRM 应用于更强的 MLLM（GPT‑4.1‑mini、o4‑mini），也观察到一致的 Best‑of‑N 增益，在 MathVista 上 o4‑mini + DreamPRM 达 85.2% 准确率，升至排行榜第一（截至 2025‑10‑15）。  
- **额外对比**（表 5）：在 o4‑mini 骨干上对比自一致性、ORM、Vanilla‑PRM，DreamPRM 以 85.2% 显著领先。  
- **充分性与公平性**：实验覆盖数学和通用推理共 5 个基准，对比了零样本、测试时缩放、多种 PRM 基线；消融实验完整；所有设置均在同一基线和推理条件下进行，对比公平。

## 6. 论文的主要结论与发现

1. DreamPRM 的领域重加权策略显著优于无数据选择（Vanilla PRM）和手工规则选择（s1‑PRM、CaR‑PRM），在 5 个基准上平均提升约 2%~4%。  
2. 与零样本 SOTA 模型（GPT‑4v、Gemini‑1.5‑Pro）和测试时缩放方法（自一致性、自纠正、ORM）相比，DreamPRM 取得最高准确率，证明高质量的 PRM 是测试时缩放成功的关键。  
3. DreamPRM 在 MathVista 排行榜上以 85.2% 准确率（o4‑mini 骨干）取得第一名，展示了极强泛化能力。  
4. 学习到的领域权重与数据集质量高度相关：高质量、难度大的领域获得更大权重，简单噪声领域被抑制。  
5. DreamPRM 具有良好的缩放能力（更多 CoT 候选带来更好结果）和跨模型泛化能力（可提升 GPT‑4.1‑mini 和 o4‑mini）。

## 7. 优点

- **自动化数据选择**：无需手工规则，通过双层次优化自动学习领域权重，可扩展且适应性更强。  
- **定制化上层损失**：提出聚合函数损失（Aggregation Function Loss）直接优化推理时的最终选择目标，比直接使用 MSE 训练损失更契合推理场景。  
- **强泛化性**：不仅在单一骨干上有效，还能转移至更强的闭源 MLLM，并在多个不同类型基准上一致提升。  
- **公开可复现**：代码、权重、评估脚本将全部开源，便于社区使用和进一步研究。  
- **对数据不平衡问题的深刻分析**：通过可视化领域权重和案例（图 1、图 7）直观说明方法如何识别并优先处理关键数据。

## 8. 不足与局限

- **计算开销**：蒙特卡罗信号采样需要多次 MLLM 推理，加之双层次优化需要交替计算，整体训练成本较高（单 A100 约 10 小时）。  
- **固定领域假设**：当前假设训练集由预定义的 K 个领域组成，未探索实例级（instance‑level）重加权或动态领域扩展。  
- **蒙特卡罗采样效率**：文中提到了动态采样策略，但未对采样效率做深入优化分析，可能仍有提升空间。  
- **实验覆盖有限**：虽然评估了 5 个基准，但未在更多复杂多模态任务（如视频理解、文档布局分析等）上验证；消融实验只报告了单次运行，未给出置信区间或误差条（论文承认未报告）。  
- **对元数据集质量依赖**：上层优化依赖一个较高质量的元数据集（MMMU），若元数据集本身存在偏差或质量下降，可能影响最终权重学习。  
- **未与最新推理模型对比**：论文提交时（NeurIPS 2025），部分更先进的 MLLM 可能已发布，但未包含在对比中（如 GPT‑4o 后代、Claude 3.5 等）。

（完）
