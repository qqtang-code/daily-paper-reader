---
title: "Let Me Think! A Long Chain of Thought Can Be Worth Exponentially Many Short Ones"
title_zh: 让我思考！长链推理可以等价于指数多个短链
authors: "Parsa Mirtaheri, Ezra Edelman, Samy Jelassi, Eran Malach, Enric Boix-Adserà"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=GuvQJGgbLm"
tags: ["query:mm-cot"]
score: 7.0
evidence: 长链推理优势的理论分析
tldr: 该论文理论证明了在特定图推理问题中，长链式推理（顺序缩放）相比并行短链（多数投票）具有指数级优势。通过图连通性问题验证了理论，为推断时计算分配提供了新视角。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-guvqjggblm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1416, \"height\": 518, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guvqjggblm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1553, \"height\": 251, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guvqjggblm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guvqjggblm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1416, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guvqjggblm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1425, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guvqjggblm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1412, \"height\": 928, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guvqjggblm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1420, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guvqjggblm/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1401, \"height\": 511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guvqjggblm/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1111, \"height\": 662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guvqjggblm/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1394, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guvqjggblm/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1011, \"height\": 561, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guvqjggblm/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 998, \"height\": 658, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-guvqjggblm/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1276, \"height\": 638, \"label\": \"Figure\"}]"
motivation: 推理时计算的最优分配方式（顺序缩放 vs 并行缩放）尚不清楚。
method: 通过图连通性问题理论证明长链推理的指数级优势，并实验验证。
result: 在挑战性图分布中，长链推理显著优于并行短链。
conclusion: 顺序缩放（长链）在某些推理场景中比并行缩放更有效。
---

## Abstract
Inference-time computation has emerged as a promising scaling axis for improving large language model reasoning. However, despite yielding impressive performance, the optimal allocation of inference-time computation remains poorly understood. A central question is whether to prioritize sequential scaling (e.g., longer chains of thought) or parallel scaling (e.g., majority voting across multiple short chains of thought). In this work, we seek to illuminate the landscape of test-time scaling by demonstrating the existence of reasoning settings where sequential scaling offers an exponential advantage over parallel scaling. These settings are based on graph connectivity problems in challenging distributions of graphs. We validate our theoretical findings with comprehensive experiments across a range of language models, including models trained from scratch for graph connectivity with different chain of thought strategies as well as large reasoning models.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义（研究动机和背景）

大语言模型（LLM）的推理能力近年来通过增加**推理时计算**（inference-time compute）获得显著提升，例如 OpenAI o1、DeepSeek-R1 等模型。然而，如何最优分配推理时计算资源仍不清楚。核心问题在于：是优先使用**顺序缩放**（sequential scaling，即生成更长的思维链 Chain-of-Thought），还是**并行缩放**（parallel scaling，即生成多条短思维链后进行多数投票或“best-of-n”选择）？

本文以**图连通性问题**为代理任务，证明在某些推理场景下，顺序缩放（长CoT）在效率上**指数级优于**并行缩放（大量短CoT）。该发现挑战了“通过并行短链可等价替代长链”的常识，揭示了推理时计算分配的根本性原则。

### 论文方法论：核心思想与关键技术细节

论文结合理论证明与抽象模型分析，提出两组关键证据：

1. **基于Transformer表达力限制的分离定理（Theorem 1/4）**  
   - **假设**：复杂度理论中 TC⁰ ⊉ L（即对数空间复杂度类L无法被阈值电路TC⁰可计算）。  
   - **顺序缩放成功**：存在常数c，使得一个多项式精度Transformer使用长度 ≤ nᶜ 的CoT即可解决任意规模的(s,t₁,t₂)-连通性问题（可模拟广度优先搜索）。  
   - **并行缩放失败**：对于任意常数C₁、C₂，若并行生成 ≤ n^{C₁} 条长度 ≤ C₂ 的短CoT，通过多数投票得到的正确率 ≤ 1/2 + o(1)。即并行缩放需要超多项式数量的短链才能逼近一条长链的能力。  
   - **证明技巧**：利用已有结论——定深度Transformer属于TC⁰类；多数投票仍可用TC⁰电路近似；并构造TC⁰归约将(s,t)-连通性转化为(s,t₁,t₂)-连通性。

2. **基于顶点查询模型（Vertex Query Model, VQM）的精细分离**  
   - **VQM抽象**：假设带有CoT的Transformer在图上推理时，每一步只能查询当前顶点的邻居（局部计算），这对应于CoT的每一时刻输出一个相邻顶点。  
   - **两径图（Two-Path）**：证明任何VQM算法若要正确区分两个不连通的路径，必须执行Ω(L)次查询（对应长CoT），否则成功概率仅为1/2；而长度为L-1的查询序列可完美解决。  
   - **桥图（Bridge Graph）**：构造更复杂的图结构（深度d，交替短路径/长路径/死胡同），证明在受限VQM下，即使查询次数略多于最短路径长度，并行缩放也需要指数级次数的独立运行才能接近顺序缩放的成功概率；而顺序缩放仅需 (1+δ)2ld 次查询即可高概率成功（l为路径参数）。

### 实验设计：数据集、场景与对比方法

- **核心任务**：(s,t₁,t₂)-连通性，输入为无向图边列表和三个顶点，要求判断s与t₁还是t₂连通（保证恰好一个连通）。  
- **图生成**：采用“桥图（Bridge(d,3,5,3)）”和“两径图”两类挑战性分布，顶点标签随机置换，边顺序随机打乱。  
- **训练的模型**：  
  - 从零训练的**小型Transformer**（Mistral架构：4隐藏层、4注意力头、中间维度128），上下文长度400。  
  - 训练使用不同CoT策略生成的数据集：最短路径（Shortest-Path）、路径（Path）、深度优先搜索（DFS）、随机游走（Walk-L）等。  
- **评估的大模型**：DeepSeek-R1-Distill-Qwen-32B、Qwen3-32B、s1-32B。  
- **对比方法**：  
  - 顺序缩放：逐步延长CoT长度（budget forcing）。  
  - 并行缩放：多数投票（Majority Vote）和最佳-n（Best-of-n）。  
- **评价指标**：决策准确率（Decision Accuracy）和证据准确率（Evidence Accuracy，要求CoT是有效路径证明）。

### 资源与算力

- 小型Transformer训练：每实验使用1块NVIDIA A100 GPU（40GB），预训练≤12小时，RL微调≤3小时，超参数调优≤72小时。  
- 大模型实验：AIME2024实验使用H200 GPU（约1.5小时/run，总计24 H200 GPU小时）；图连通性实验使用2块A100 GPU（80GB），通过vllm推理，每图<4小时，总计<120 GPU小时。

### 实验数量与充分性

- 从小规模深度1~6的桥图到大规模深度5的桥图，覆盖多个难度级别。  
- 对比多种CoT策略（Shortest-Path、Path、DFS、DFS-BT、Walk-L等），并进行了RL迭代（STaR方法）。  
- 大模型测试涵盖三种主流开源推理模型，并额外在AIME2024数学竞赛题上验证。  
- 实验包含误差线（95% binomial confidence intervals），结果统计可靠。  
- **充分性**：验证了理论预测的指数级分离，在小模型和大模型上均观察到一致趋势。但缺乏对模型规模、不同架构（如MoE）的全面消融。

### 主要结论与发现

1. **顺序缩放（长CoT）在图连通性任务中显著优于并行缩放**：即使并行生成指数级短链，也无法达到一条适当长度的长链的准确率。  
2. **短CoT模型的行为类似随机搜索**：训练于最短路径的模型只能以指数小概率成功，其准确率与随机游走中走对路径的概率一致。  
3. **强化学习（STaR）可自然诱发CoT长度增长**：模型通过RL迭代，CoT长度逐渐增加，准确率大幅提升，这与DeepSeek-R1等前沿模型的行为一致。  
4. **大模型在AIME2024上也表现出对顺序缩放的依赖**：增加CoT长度比大量并行投票更有效。

### 优点

- **理论严密**：基于复杂度假设给出严格分离定理，并通过抽象模型（VQM）得到精细的下界。  
- **实验设计全面**：从零训练的小模型到前沿大模型，覆盖多种CoT策略，并与理论预测高度吻合。  
- **新颖视角**：将推理时计算分配问题形式化为顺序与并行的权衡，并首次证明指数级优势的存在。

### 不足与局限

- **依赖复杂度假设**：TC⁰ ⊉ L 尚未被证明，理论分离结果仅在假设下成立。  
- **VQM抽象未必完全等价**：实际Transformer可能具备比VQM更强的能力（如全局注意力跨越局部限制）。  
- **实验覆盖有限**：仅在图连通性任务上深入验证；AIME2024实验较为初步。  
- **并行缩放的表现可能随问题而异**：论文承认最优混合策略可能问题依赖，本文未给出普适规则。  
- **未考虑实际成本**：顺序缩放虽计算效率高，但上下文窗口二次增长在极长CoT下可能不经济。

（完）
