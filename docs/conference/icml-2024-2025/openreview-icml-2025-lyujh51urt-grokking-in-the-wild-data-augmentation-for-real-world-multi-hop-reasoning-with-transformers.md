---
title: "Grokking in the Wild: Data Augmentation for Real-World Multi-Hop Reasoning with Transformers"
title_zh: 野外涌现：基于数据增强的真实世界多跳推理
authors: "Roman Abramov, Felix Steinbauer, Gjergji Kasneci"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=lyUJH51URt"
tags: ["query:mm-cot"]
score: 6.0
evidence: 将grokking扩展到真实世界多跳推理，通过数据增强实现
tldr: 以往grokking研究局限于小规模合成任务，本文首次将其扩展到真实世界多跳事实推理。通过精心设计的合成数据增强知识图谱，提高推理事实与原子事实的比率，使模型从记忆转向泛化。实验结果显示，该方法有效提升了多步推理能力，为长链推理的数据稀缺问题提供了解决方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-lyujh51urt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 850, \"height\": 507, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lyujh51urt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 726, \"height\": 234, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lyujh51urt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 783, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lyujh51urt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1760, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lyujh51urt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 723, \"height\": 571, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-lyujh51urt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 878, \"height\": 413, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lyujh51urt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 887, \"height\": 387, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lyujh51urt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 887, \"height\": 349, \"label\": \"Table\"}]"
motivation: 现有grokking研究仅用于合成数据，真实世界多步推理泛化困难。
method: 通过增强知识图谱中合成数据提升推理事实比例，触发grokking。
result: 首次在真实数据上实现grokking，显著提升多跳推理性能。
conclusion: 数据增强可激活grokking，助力真实世界多步推理任务。
---

## Abstract
Transformers have achieved great success in numerous NLP tasks but continue to exhibit notable gaps in multi-step factual reasoning, especially when real-world knowledge is sparse. Recent advances in grokking have demonstrated that neural networks can transition from memorizing to perfectly generalizing once they detect underlying logical patterns -- yet these studies have primarily used small, synthetic tasks. In this paper, for the first time, we extend grokking to real-world factual data and address the challenge of dataset sparsity by augmenting existing knowledge graphs with carefully designed synthetic data to raise the ratio $\phi_r$ of inferred facts to atomic facts above the threshold required for grokking. Surprisingly, we find that even factually incorrect synthetic data can strengthen emergent reasoning circuits rather than degrade accuracy, as it forces the model to rely on relational structure rather than memorization. When evaluated on multi-hop reasoning benchmarks, our approach achieves up to 95--100\% accuracy on 2WikiMultiHopQA -- substantially improving over strong baselines and matching or exceeding current state-of-the-art results. We further provide an in-depth analysis of how increasing $\phi_r$ drives the formation of generalizing circuits inside Transformers. Our findings suggest that grokking-based data augmentation can unlock implicit multi-hop reasoning capabilities, opening the door to more robust and interpretable factual reasoning in large-scale language models.

---

## 论文详细总结（自动生成）

# 论文《Grokking in the Wild: Data Augmentation for Real-World Multi-Hop Reasoning with Transformers》详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：Transformer 在自然语言处理任务中表现优异，但在需要多步事实推理（multi-hop reasoning）的场景下仍然存在显著不足，尤其当真实世界知识稀疏时，模型容易陷入记忆而非泛化。
- **背景**：先前关于“grokking”（神经网络从记忆到完美泛化的突然转变）的研究主要局限于小规模合成任务（如模算术、算法数据集）。本文首次尝试将 grokking 扩展到真实世界的事实数据上。
- **核心挑战**：真实世界的知识图谱通常稀疏且不完整，导致推理事实（inferred facts）与原子事实（atomic facts）的比率 φ 过低，无法触发泛化电路的形成。因此，关键问题是如何通过数据增强来提高 φ 值，使得 Transformer 能够内部形成多跳推理电路。

## 2. 方法论

### 2.1 核心思想

- 通过**系统地添加合成数据**（包括正确的甚至故意不正确的合成事实）来扩充原始知识图谱，从而提高每个关系的推理事实与原子事实之比 φr，使其超过触发 grokking 的阈值（经验阈值约 3.6~6.25）。
- 该方法不依赖显式的链式思维提示（chain-of-thought），而是让模型在训练中逐步形成内部泛化电路，从而实现隐式推理（implicit reasoning）。

### 2.2 关键技术细节

- **定义**：知识图谱 KG = (V, R, FA)，其中原子事实 FA 为 (h, r, t) 三元组；推理事实 FI 为长度≥2 的多跳路径。关系特定的泛化比率 φr = |FI,r| / |FA,r|。
- **数据增强流程**：
  1. **比较任务（Comparison）**：先通过 LLM 生成新的地理位置原子事实（如城市-国家对），再由这些原子事实系统地组合成比较型推理问题（如“A 和 B 是否位于同一个国家？”）。初始 120 原子+60 推理 → 增强至 1000 原子+8000 推理，φ=8。
  2. **组合任务（Composition）**：将文本事实解析为图结构，通过 LLM 提取节点和边，然后按需添加新的原子边（避免循环），并采样多跳路径生成推理问题（如“谁的爸爸的出生地？”）。初始 200 原子+100 推理 → 800 原子+5000 推理，φ=6.25。
- **算法**：Algorithm 1（比较任务）和 Algorithm 2（组合任务）详细描述了增强步骤，包括生成原子事实、详细化段落、以及基于图结构的推理事实生成。

### 2.3 理论支持

- **引理 1**：给出了 n 跳路径数量的渐近上限，表明 φr 在自然稀疏图中受限于 b^(n-1)，其中 b 为分支因子。
- **引理 2**：推导了完全泛化所需的最小关系特定分支因子，指出若任一关系的 br 低于阈值，则知识库无法完全泛化。

## 3. 实验设计

### 3.1 数据集

- **主要数据集**：2WikiMultiHopQA（基于 Wikipedia 的多跳 QA 基准），分为结构化（简化为三元组）和非结构化（完整段落）两个子集。
- **评估任务**：比较任务（Comparison，比较两个实体的共享属性）和组合任务（Composition，链式推理）。
- **评价指标**：In-distribution (ID) 准确率和 Out-of-distribution (OOD) 准确率，grokking 的标志是 OOD 准确率在长时间训练后突然跳跃。

### 3.2 对比方法

- **基线**：未经增强的原始 GPT-2 Small（1.24 亿参数）在原始数据集上训练。
- **对照**：GPT-4o 和 o1-mini 在相同结构化数据集上评测（但无法严格区分 ID/OOD，因为它们的预训练数据已包含大量 Wikipedia 知识）。
- **本文方法**：在增强数据集上训练的相同 GPT-2 Small 模型（称为“Grokked GPT-2 Small”）。

## 4. 资源与算力

- **模型**：8 层 GPT-2 风格 Transformer，隐藏单元 768，12 注意力头。
- **优化器**：AdamW，学习率 5×10⁻⁵，批大小 512，权重衰减 1。
- **训练**：最多约 30 万步，直到出现 OOD 准确率跃升。使用 bf16 精度和 torch compile。
- **硬件**：单张 NVIDIA A100 GPU，每轮实验约 48 小时，共使用三个随机种子，报告最佳结果（差异 ±1–2%）。
- **备注**：文中未明确提及训练的总 GPU 小时数（例如 3 个种子 × 48 小时 = 144 小时），但已有足够信息。

## 5. 实验数量与充分性

- **实验组数**：包括结构化比较任务、结构化组合任务、非结构化比较任务，以及原始无增强的对比实验（共 4 组主要训练曲线，如图 4 所示）。还有与 GPT-4o/o1-mini 的对比表（表 3）。
- **消融实验**：论文通过对比有无数据增强来验证 φ 值的作用，但未进行系统性的 φ 值梯度消融（如不同 φ 水平的对比）。
- **公平性与客观性**：
  - 与 GPT-4o/o1-mini 的对比存在固有偏差：这些模型的预训练数据已包含大量 Wikipedia 知识，难以严格界定 ID/OOD。论文承认了这一点。
  - GPT-2 Small 从头训练，而商业模型是预训练的，比较并非完全对等。
  - 实验覆盖了两种任务类型和两种数据格式，但对更长推理链（如 3 跳以上）的测试不足。
  - 整体实验设计合理，结论可信，但缺乏在更多样化基准（如 MuSiQue、HotpotQA）上的验证。

## 6. 主要结论与发现

1. **grokking 可在真实数据上实现**：通过数据增强提高 φr，Transformer 能够从记忆转向泛化，在 2WikiMultiHopQA 比较任务上达到近乎 100% 的 OOD 准确率，甚至超越 GPT-4o 和 o1-mini。
2. **即使不正确的合成数据也有益**：令人惊讶的是，添加事实错误的数据反而强化了推理电路，因为它迫使模型依赖关系结构而非记忆。
3. **关系特异性阈值**：不同关系需要不同的 φr 阈值；组合任务中的复杂关系更难泛化，结构化数据下的 OOD 准确率仅 7%。
4. **非结构化文本增加难度**：完整段落中的噪声和长文本降低了收敛速度并限制了 OOD 改善。

## 7. 优点

- **开创性**：首次将 grokking 从合成任务扩展到真实世界的事实推理数据集，具有重要研究价值。
- **方法简洁有效**：仅通过数据增强调整数据分布即可引发模型内部泛化电路，无需修改模型架构或增加推理阶段。
- **理论支撑**：提供了引理和上界分析，解释了 φr 与泛化能力之间的关系。
- **鲁棒性发现**：不正确的合成数据仍能提升泛化，提示模型更关注结构而非记忆，对低质量数据有一定容忍度。
- **透明性**：公开了数据增强算法（Algorithm 1 & 2）和训练细节，易于复现。

## 8. 不足与局限

- **实验覆盖有限**：
  - 仅在 2WikiMultiHopQA 一个数据集上验证，未在 MuSiQue、HotpotQA、或者需要更长推理链（3 跳以上）的基准上测试。
  - 仅考察了比较和组合两种任务，未涉及时间推理、常识推理等更复杂模式。
- **组合任务泛化失败**：在结构化组合任务中 OOD 准确率仅 7%，说明方法对链式推理的内部电路形成仍不充分。
- **稀有关系与消歧问题**：低频关系或实体歧义（如重名）仍会导致失败，需要更精细的数据增强或消歧策略。
- **事实性与幻觉风险**：合成数据可能引入事实错误，虽然在实验中未显著影响平均准确率，但在高可靠性场景（医疗、法律）中可能有严重风险。
- **计算成本高**：需要数十万步训练（单卡 48 小时），且 grokking 发生时间不固定，实际部署成本较高。
- **与预训练模型比较不严格**：GPT-4o/o1-mini 的 ID/OOD 难以界定，削弱了对比结论的绝对说服力。
- **可解释性不足**：虽然观察到了泛化电路形成，但内部机制（如注意力头如何实现关系链接）未做深入机械解读。

（完）
