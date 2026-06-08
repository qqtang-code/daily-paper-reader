---
title: Rethinking Chain-of-Thought from the Perspective of Self-Training
title_zh: 从自训练角度重新思考思维链
authors: "Zongqian Wu, Baoduo Xu, Ruochen Cui, Mengmeng Zhan, Xiaofeng Zhu, Lei Feng"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=ksdPdnwKGi"
tags: ["query:mm-cot"]
score: 9.0
evidence: 从自训练角度重新思考思维链
tldr: 该论文观察到思维链推理与自训练具有共同目标，即逐步利用模型生成信息减少不确定性。基于此，提出一种新的思维链框架，包含任务特定提示模块和自适应推理迭代模块，以优化初始推理过程并动态调整推理步骤。实验证明该框架能有效缓解过度推理和连续迭代高度相似的问题，提升了推理性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ksdpdnwkgi/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 851, \"height\": 719, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ksdpdnwkgi/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 822, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ksdpdnwkgi/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 850, \"height\": 328, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ksdpdnwkgi/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1703, \"height\": 863, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ksdpdnwkgi/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 854, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ksdpdnwkgi/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1739, \"height\": 693, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ksdpdnwkgi/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1651, \"height\": 689, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ksdpdnwkgi/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1645, \"height\": 710, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ksdpdnwkgi/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1774, \"height\": 550, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ksdpdnwkgi/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 855, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ksdpdnwkgi/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1695, \"height\": 639, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ksdpdnwkgi/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1766, \"height\": 544, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ksdpdnwkgi/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 986, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ksdpdnwkgi/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1761, \"height\": 711, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ksdpdnwkgi/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1761, \"height\": 713, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ksdpdnwkgi/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1748, \"height\": 2361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ksdpdnwkgi/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1756, \"height\": 2017, \"label\": \"Table\"}]"
motivation: 发现思维链推理与自训练在目标上的共性，旨在改进CoT推理的性能。
method: 提出融合任务特定提示和自适应推理迭代的CoT框架，动态优化推理过程。
result: 新框架有效缓解了CoT中的过度推理和迭代相似性问题，提升了推理性能。
conclusion: 为改进CoT推理提供了新视角，并通过模块化设计实现了显著提升。
---

## Abstract
Chain-of-thought (CoT) reasoning has emerged as an effective approach for activating latent capabilities in LLMs. Interestingly, we observe that both CoT reasoning and self-training share the core objective: iteratively leveraging model-generated information to progressively reduce prediction uncertainty. Building on this insight, we propose a novel CoT framework to improve reasoning performance. Our framework integrates two key components: (i) a task-specific prompt module that optimizes the initial reasoning process, and (ii) an adaptive reasoning iteration module that dynamically refines the reasoning process and addresses the limitations of previous CoT approaches, i.e., over-reasoning and high similarity between consecutive reasoning iterations. Extensive experiments show that the proposed method achieves significant advantages in both performance and computational efficiency. Our code is available at: https://github.com/zongqianwu/ST-COT.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：论文观察到**思维链（Chain-of-Thought, CoT）推理**与**自训练（Self-Training）** 存在深层共性：两者都**迭代地利用模型自身生成的信息（CoT中的中间推理步骤、自训练中的伪标签）来逐步降低预测不确定性**。基于这一洞察，作者试图将自训练的理论和实践经验迁移到CoT中，从而改进CoT的推理性能。
- **核心问题**：现有CoT方法存在两大瓶颈——**过度推理**（correct predictions turn incorrect after multiple rounds）和**连续迭代之间的推理高度相似**（high similarity between consecutive reasoning iterations），导致推理效果和效率下降。本文旨在解决这些问题。

---

### 2. 方法论：核心思想、关键技术细节
- **核心思想**：将CoT视为一个**不确定性最小化过程**，类比自训练。在此基础上设计两个互补模块：
  1. **任务特定提示模块（Task-Specific Prompt, TSP）**  
      - 目的：替代通用的“Let’s think step by step”提示，生成与任务特征更匹配的初始推理。  
      - 流程：  
        - 从数据集采样一个子集 \(Q'\)，结合指令让LLM生成 \(m\) 个候选提示 \(P=\{p_1,...,p_m\}\)。  
        - 用另一个不相交子集 \(Q''\) 计算每个候选提示下的**语义熵**（Semantic Entropy），选择熵最低的提示 \(\hat{p}\)。  
        - 低语义熵对应更准确的初始推理，从而减少后续迭代次数。
  2. **自适应推理迭代模块（Adaptive Reasoning Iteration, ARI）**  
      - 目的：动态决定是否继续推理，并解决过度推理和迭代相似性问题。  
      - 流程：  
        - 用 \(\hat{p}\) 生成初始推理集 \(R'_i\) 和预测集 \(A'_i\)，计算语义熵 \(e'_i\)。  
        - **若 \(e'_i \le \delta\)（低不确定性）**，则直接输出当前预测，停止迭代（避免过度推理）。  
        - **若 \(e'_i > \delta\)**，则引入一个新提示 \(p^*\)（鼓励从不同角度推理），结合历史推理和预测，生成新的推理集 \(R''_i\)。  
        - 计算新推理与旧推理的**Jaccard相似度** \(s''_i\)，若高于阈值 \(\tau\) 则重新采样，确保多样性。  
        - 基于 \(R''_i\) 生成新预测 \(A''_i\)，重复上述过程直到熵低于 \(\delta\) 或达到最大迭代次数 \(T\)。  
      - 若 \(T\) 后熵仍高，则对全部迭代的预测进行**多数投票**作为最终输出。

- **关键公式**：  
  - 语义熵近似：\(\hat{e} = -\sum_{j=1}^k g_j \log g_j\)，其中 \(g_j = |C_j|/N\)。  
  - Jaccard相似度：\(s''_i = \frac{|R''_i \cap R'_i|}{|R''_i \cup R'_i|}\)。

- **理论支撑**：论文通过高斯混合模型下的理论分析（Lemma 3.1, Theorem 3.2）证明了自训练中熵的四种变化模式，并类比到CoT中的语义熵变化（结论(i)-(v)），为方法设计提供依据。

---

### 3. 实验设计：数据集、基准、对比方法
- **数据集**：10个推理数据集，分为三类：
  - **算术**：MultiArith、GSM8K、SingleEq、AddSub、AQuA、SVAMP  
  - **常识推理**：StrategyQA、CommonsenseQA  
  - **符号推理**：LastLetter、CoinFlip
- **基准方法**：
  - Zero-Shot（直接提问）  
  - Zero-Shot-CoT（通用提示+贪心解码）  
  - Zero-Shot-CoT + Self-Consistency（SC，采样+投票）  
  - RE2、RE2 + SC  
  - Contrastive-CoT（少样本）  
  - Few-Shot、Few-Shot-CoT（少样本设置）
- **实验设置**：
  - 基础模型：GPT-3.5-turbo-0125  
  - 零样本任务：全部10个数据集  
  - 少样本任务：MultiArith和GSM8K  
  - 采样数 \(N=3\)；最大迭代次数 \(T=5\)（默认3）；阈值 \(\delta\) 和 \(\tau\) 通过验证集确定。
- **评估指标**：准确率（Accuracy）

---

### 4. 资源与算力
- 论文**未明确说明所使用的GPU型号、数量、训练时长**。  
- 仅提及使用GPT-3.5-turbo-0125作为基础模型，并给出了迭代时间成本（图5：在AQuA上，5次迭代耗时约4.3小时），但未提供硬件细节。  
- 因此，算力信息不够透明。

---

### 5. 实验数量与充分性
- **实验数量**：丰富且系统。  
  - **主实验**：零样本10个数据集上对比5种方法（表1）。  
  - **少样本实验**：2个数据集上对比Few-Shot/CoT系列方法（表2）。  
  - **消融实验**：分别评估TSP、ARI及两者结合的效果（表1各子行）。  
  - **参数敏感性**：迭代次数 \(T\)（1-5）和采样数 \(N\)（1-7）的影响（图5、图7）。  
  - **自适应vs固定迭代**：准确率与时间成本对比（图5）。  
  - **相似度度量**：通用提示与所提提示\(p^*\)下迭代间相似度（表5）。  
  - **案例分析**：附录中提供了多个示例（表6-9）具体说明如何解决过度推理和相似性问题。
- **充分性与公平性**：
  - 对比方法覆盖主流CoT变体，且使用相同的SC采样数（3）确保公平。  
  - 消融实验清晰分离了TSP和ARI的贡献。  
  - 但少样本实验仅选了两个算术数据集，覆盖不够广泛；常识和符号任务未在少样本设置下测试。  
  - 部分消融（如不同阈值 \(\delta, \tau\) 的影响）在正文中缺失，依赖附录中的案例说明。

---

### 6. 主要结论与发现
- **性能提升**：所提ST-CoT框架在零样本任务上平均准确率从79.5%（Zero-Shot-CoT+SC）提升至**83.7%**（+4.2%）；在少样本任务上从85.5%提升至**87.4%**（+1.9%）。  
- **缓解过度推理**：通过语义熵阈值 \(\delta\) 停止进一步迭代，避免了正确预测被后续噪声干扰。  
- **增强迭代多样性**：新提示 \(p^*\) 和 Jaccard相似度约束有效降低连续迭代间的相似度（从0.38降至0.29），使LLM探索不同推理路径。  
- **计算效率**：自适应迭代比固定迭代更早达到稳定高精度，节省时间（例如5次迭代耗时4.3h vs 6.5h）。  
- **理论贡献**：首次将自训练中的熵分析框架迁移至CoT，为理解其迭代机制提供了新视角。

---

### 7. 优点：方法或实验设计上的亮点
- **创新性**：发现CoT与自训练的本质联系，并利用这一视角系统性设计改进，思路新颖。  
- **问题导向**：直接针对现有CoT的两大缺陷（过度推理、迭代相似）提出明确解决方案，可解释性强。  
- **模块化设计**：TSP和ARI可独立或组合使用，能够即插即用于不同CoT方法（零样本和少样本均适用）。  
- **实验全面性**：覆盖零样本和少样本、多种推理类型、消融、参数敏感性和实际案例，论证充分。  
- **实用平衡**：在准确率和计算成本之间取得良好平衡，通过自适应停止策略避免了冗余迭代。

---

### 8. 不足与局限
- **常识推理提升有限**：在StrategyQA和CommonsenseQA上，性能增长微弱（约1-2%），甚至有时低于零样本基线。作者指出这可能是由于此类任务依赖预训练阶段已编码的知识，深度推理难以弥补知识缺失。  
- **少样本实验范围窄**：仅使用两个算术数据集，未在更多少样本场景（如符号推理）下验证ARI的通用性。  
- **资源消耗不透明**：未报告GPU型号、显存需求、总训练/推理时间，难以复现或公平比较计算开销。  
- **阈值设定依赖验证集**：\(\delta\) 和 \(\tau\) 需要在验证集上调整，可能影响在不同任务上的泛化；论文未给出具体阈值选择策略。  
- **最大迭代次数后的处理**：当熵始终高于 \(\delta\) 时使用多数投票，可能混合了错误和正确预测，该策略的理论依据不足。  
- **单模型测试**：仅用GPT-3.5-turbo，未验证在GPT-4、Llama等其他LLM上的效果，可推广性有待验证。  
- **理论分析部分**：虽然提供了高斯混合模型下的熵分析，但映射到CoT语义熵时仍基于较强假设（Assumption 3.7），实际推理树中的错误传播可能更复杂。

---

（完）
