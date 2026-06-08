---
title: "DLoFT: Gradient-Decoupled Fine-Tuning for Generalizable Long Chain-of-Thought Reasoning"
title_zh: DLoFT：面向泛化长链推理的梯度解耦微调
authors: "Sitong Wu, Haoru Tan, Jingyao Li, Shaofeng Zhang, XIAOJUAN QI, Bei Yu, Jiaya Jia"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=5ZDT1dxojA"
tags: ["query:mm-cot"]
score: 8.0
evidence: 梯度解耦微调实现泛化长链推理
tldr: 监督微调长链推理易过拟合问题特定知识导致泛化差。提出DLoFT算法，将长链推理能力与问题内容解耦，通过梯度解耦训练使模型学习通用推理策略，在多个分布外测试集上维持高推理性能，为长链推理的鲁棒泛化提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1368, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1422, \"height\": 878, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 407, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1429, \"height\": 810, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1444, \"height\": 522, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1332, \"height\": 978, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5zdt1dxoja/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1337, \"height\": 565, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-5zdt1dxoja/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1041, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5zdt1dxoja/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1349, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5zdt1dxoja/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1092, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-5zdt1dxoja/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1036, \"height\": 194, \"label\": \"Table\"}]"
motivation: 长链推理的监督微调易过拟合问题特定知识，泛化能力弱。
method: 提出梯度解耦算法分离推理能力与内容特征。
result: 在多个分布外数据集上推理准确率提升显著。
conclusion: DLoFT有效增强了长链推理的泛化性。
---

## Abstract
Long chain-of-thought (LongCoT) has emerged as a powerful reasoning paradigm for enabling large language models (LLMs) to solve complex tasks through a systematic and thorough thinking phase.
Although supervised fine-tuning (SFT) on high-quality LongCoT traces has proven effective to activate LongCoT abilities, we find that models trained in this way tend to overfit problem-specific knowledge and heuristics, leading to degraded out-of-distribution performance.
To address this issue, we propose a Decoupled LongCoT Fine-Tuning (DLoFT) algorithm, which enables the model to learn generalizable LongCoT reasoning abilities while preventing overfitting to the reasoning content with problem-specific information.
The key idea is to decouple the gradient into two orthogonal components: 1) a paradigm-relevant gradient corresponding to the general LongCoT paradigm and 2) a content-relevant gradient reflecting the problem-specific information, where only the former gradient is used to update model parameters.
Specifically, by leveraging the unique two-phase composition (thinking and solution) of the LongCoT response, our gradient decoupling mechanism isolates the content-relevant gradient via a projection operation and separates the paradigm-relevant gradient through orthogonalization.
Our DLoFT ensures the model concentrate on internalizing the LongCoT paradigm rather than memorizing problem-specific knowledge and heuristics.
Extensive experiments demonstrate that our DLoFT significantly improves the generalization behavior of LongCoT abilities compared to SFT while maintaining strong in-distribution performance.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：长链思维（LongCoT）推理能力能够显著提升大语言模型（LLM）在复杂任务上的表现，但现有的监督微调（SFT）方法在高质量 LongCoT 数据上训练时，容易过拟合训练数据中的**问题特定知识**和**启发式策略**，导致模型在分布外（out-of-distribution）任务上的泛化性能严重下降。
- **研究动机**：实际场景中，为每个领域构建大规模、高质量的 LongCoT 数据集成本极高甚至不可行。作者希望让模型仅从少量代表性数据中学习到**通用的 LongCoT 推理范式**，而非记忆具体的解题知识，从而实现对不同领域的良好泛化。
- **整体含义**：本文提出了一种新的训练算法 DLoFT，通过梯度解耦分离推理范式相关梯度与问题内容相关梯度，并仅用前者更新模型参数，从而在保持分布内性能的同时大幅提升分布外泛化能力。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
利用 LongCoT 响应固有的**两阶段结构**（思考阶段 + 解题阶段）来辅助梯度解耦：思考阶段同时包含推理范式和问题特定信息，而解题阶段主要包含问题特定信息。通过比较完整响应梯度和单独解题阶段梯度，分离出问题内容相关梯度，进而通过正交化得到范式相关梯度。

### 关键技术细节（算法流程）
1. **计算完整响应梯度 \( g_{\text{full}} \)**：对完整 LongCoT 响应（思考阶段 \(\oplus\) 解题阶段）计算负对数似然（NLL）损失并求梯度。
2. **计算参考梯度 \( g_{\text{ref}} \)**：仅对解题阶段 \( S \) 计算 NLL 损失并求梯度，该梯度仅包含问题特定信息。
3. **解耦问题内容相关梯度 \( g_{\text{con}} \)**：将 \( g_{\text{full}} \) 投影到 \( g_{\text{ref}} \) 上：\( g_{\text{con}} = \frac{\langle g_{\text{full}}, g_{\text{ref}} \rangle}{\|g_{\text{ref}}\|^2} \cdot g_{\text{ref}} \)。
4. **解耦范式相关梯度 \( g_{\text{par}} \)**：通过正交化从 \( g_{\text{full}} \) 中减去 \( g_{\text{con}} \)：\( g_{\text{par}} = g_{\text{full}} - g_{\text{con}} \)。
5. **更新模型参数**：仅使用 \( g_{\text{par}} \) 更新参数，避免模型记忆问题特定知识，专注于学习通用推理范式。

### 公式表述
- \( L_{\text{full}} = -\frac{1}{B} \sum_{i=1}^B \sum_{k=1}^{|T_i \oplus S_i|} \log p_\theta \left( (T_i \oplus S_i)_k \mid (T_i \oplus S_i)_{<k}, P_i \right) \)
- \( L_{\text{ref}} = -\frac{1}{B} \sum_{i=1}^B \sum_{k=1}^{|S_i|} \log p_\theta \left( S_i^k \mid S_i^{<k}, P_i \right) \)
- 最终更新：\( \theta \leftarrow \theta - \eta \cdot g_{\text{par}} \)

## 3. 实验设计

### 使用数据集
- **多领域数据集**：s1K（1000条高质量数据，覆盖数学、编程、科学、谜题等）。
- **单领域数据集**（各采样5K条）：
  - 数学：OpenR1-Math-220K → OpenR1-Math-5K
  - 代码：OpenThoughts-114K → OpenThoughts-Code-5K
  - 医学：Medical-o1 → Medical-o1-5K

### 评测基准
- **数学**：AIME24、MATH-500、OlympiadBench
- **代码**：LiveCodeBench (v2)
- **医学**：MedQA
- **其他14个领域**（物理、化学、生物、计算机、机械、电子、通信、天文、地理、土木、农业、经济、历史、法律、文学、哲学、社会学）：使用 SuperGPQA 的子集。

### 对比方法
- 主要对比：**SFT**（监督微调）与 **DLoFT**。
- 额外对比：早期停止（early stopping）、权重衰减（weight decay）、仅用内容梯度 \( g_{\text{con}} \) 更新等消融实验。
- 在强化学习（RL）冷启动阶段，对比 SFT + RL 与 DLoFT + RL。

### 模型
- 通用 LLM：Qwen2.5-Instruct（7B、32B）
- 领域专用 LLM：Qwen2.5-Math-7B-Instruct（数学）、Qwen2.5-Coder-7B-Instruct（代码）、Meditron-7B（医学）

## 4. 资源与算力

- **论文未明确说明**：文中没有提及使用的具体 GPU 型号、数量、总训练时长等信息。仅在附录 A.4 中比较了 DLoFT 与 SFT 每步训练时间和 GPU 内存（DLoFT 每步运行时间约 6.8 分钟 vs SFT 6.2 分钟，GPU 内存约 70.7 GB vs 69.9 GB），但未指出硬件型号。所有实验规模（最大 32B 模型）在通常的学术集群上可复现，但具体算力无法从论文中获取。

## 5. 实验数量与充分性

- **实验数量丰富**：涵盖了 17 个领域，使用了 3 种领域专用模型和 2 种通用模型，进行了 SFT 与 DLoFT 的全面对比。此外还有消融实验（投影操作、梯度解耦有效性、权重衰减）以及 RL 冷启动实验。
- **充分性与客观性**：
  - 控制变量：SFT 和 DLoFT 使用相同的训练设置（学习率、优化器、epoch 等）。
  - 多维度评估：不仅报告准确率，还监控 LongCoT 行为比例（使用 GPT-4o-mini 检测），分析训练动态。
  - 支持代码开源（https://github.com/dvlab-research/DLoFT），可复现性良好。
  - 消融实验验证了每个设计的必要性，实验设计较为严谨。
- **潜在不足**：未在更大规模（如 70B+ 模型）和更大数据集上验证，论文本身在限制部分承认了这一点。

## 6. 论文的主要结论与发现

1. **SFT 过拟合严重**：SFT 在分布外任务上表现持续下降（如 7B 模型在“通信”领域下降 16 点），且早期停止只能部分缓解，同时牺牲分布内性能。
2. **DLoFT 显著提升泛化**：在通用 LLM 上，DLoFT 平均提升 9.8 点（SFT 平均下降 1.8 点）；在领域专用 LLM 上，即使使用域外数据训练，DLoFT 也能接近甚至超过使用域内数据的 SFT 性能。
3. **DLoFT 作为 RL 冷启动更优**：DLoFT 可摆脱对域内 LongCoT 数据的依赖，且为后续 RL 提供更强的基础，放大 RL 收益（例如医学领域，SFT+RL 提升 3.7 点，DLoFT+RL 提升 5.0 点）。
4. **梯度解耦有效**：仅用 \( g_{\text{par}} \) 更新能使模型 100% 展现出 LongCoT 行为，而仅用 \( g_{\text{con}} \) 更新则完全不会产生 LongCoT 行为，证明了解耦机制正确分离了推理范式信号。

## 7. 优点

- **方法创新性**：首次提出利用 LongCoT 响应的两阶段结构进行梯度解耦，思路新颖，理论清晰。
- **实用性强**：仅需少量训练数据（如 5K 或 1K）即可获得强泛化能力，大幅降低数据成本。且与标准 SFT 相比，训练开销增加极小（每步仅慢 ~10%）。
- **实验全面**：覆盖 17 个领域，包括 STEM、社科、人文等，并评估了领域专用模型和通用模型，结果具有广泛代表性。
- **开源与可复现**：提供代码和数据链接，便于社区验证和后续发展。

## 8. 不足与局限

- **大模型和大规模数据验证不足**：论文仅测试到 32B 模型，未在 70B+ 或 100B+ 规模上验证；训练数据集规模也相对较小（最多 5K 域内数据）。虽然作者承认计算资源限制，但更大规模上的有效性仍需确认。
- **依赖外部分类器检测 LongCoT 行为**：使用 GPT-4o-mini 判断响应是否包含 LongCoT 行为，可能引入额外噪声和成本，且分类标准并非完全客观。
- **梯度解耦的理论保障较弱**：虽然实验证明了解耦效果，但缺乏严格的数学证明说明为什么解题阶段梯度仅包含问题特定信息，以及投影操作能完美分离两类信号（可能存在重叠）。
- **应用局限**：方法假设 LongCoT 响应具有明确的“思考+解题”两阶段结构。对于不严格遵守此格式的数据（如 CoT 无明确分割），DLoFT 可能不适用。
- **潜在风险**：作者在伦理声明中提到，该方法可能被用于强化模型的不当用途（如监控），值得关注。

（完）
