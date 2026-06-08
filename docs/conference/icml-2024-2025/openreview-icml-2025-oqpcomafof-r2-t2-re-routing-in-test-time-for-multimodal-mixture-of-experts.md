---
title: "R2-T2: Re-Routing in Test-Time for Multimodal Mixture-of-Experts"
title_zh: R2-T2：多模态混合专家的测试时路由重配
authors: "Zhongyang Li, Ziyue Li, Tianyi Zhou"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=oqPcOMafOF"
tags: ["query:multimodal"]
score: 6.0
evidence: 多模态混合专家的测试时路由重配以改善感知
tldr: 多模态大模型中视觉感知能力常弱于语言推理能力，混合专家（MoE）虽提供丰富表示但路由器不最优。本文提出R2-T2框架，在测试时重新调整路由权重，使视觉特征更适配LLM的推理需求。实验证明，该方法显著提升了模型在下游任务上的性能，且无需额外训练。该工作为多模态感知-推理差距提供了一种即插即用解决方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 859, \"height\": 779, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1551, \"height\": 693, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1764, \"height\": 665, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1771, \"height\": 906, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 865, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1768, \"height\": 784, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1765, \"height\": 737, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1775, \"height\": 777, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1583, \"height\": 802, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1768, \"height\": 790, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1766, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1770, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1763, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-oqpcomafof/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1760, \"height\": 385, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 904, \"height\": 444, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1615, \"height\": 581, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1782, \"height\": 1086, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 757, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 565, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 763, \"height\": 167, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 547, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 712, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 707, \"height\": 182, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 720, \"height\": 470, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 883, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 800, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 715, \"height\": 161, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 794, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1588, \"height\": 251, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1603, \"height\": 395, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1587, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1585, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-oqpcomafof/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1413, \"height\": 267, \"label\": \"Table\"}]"
motivation: 多模态模型中视觉感知与语言推理能力不匹配，端到端路由器可能非最优。
method: 提出测试时路由重配方法R2-T2，动态调整MoE中各专家权重以适配输入。
result: 在多个多模态基准上显著提升性能，无需重新训练。
conclusion: 该工作有效弥合了多模态感知与推理之间的鸿沟。
---

## Abstract
In large multimodal models (LMMs), the perception of non-language modalities (e.g., visual representations) is usually not on par with the large language models (LLMs)' powerful reasoning capabilities, deterring LMMs' performance on challenging downstream tasks. 
This weakness has been recently mitigated by replacing the vision encoder with a mixture-of-experts (MoE), which provides rich, multi-granularity, and diverse representations required by different downstream tasks. The performance of multimodal MoE largely depends on its router, which reweights and mixes the representations of different experts for each input. However, we find that the end-to-end trained router does not always produce the optimal routing weights for every test sample. To bridge the gap, we propose a novel and efficient method ''**R**e-**R**outing in **T**est-**T**ime (R2-T2)'' that locally optimizes the vector of routing weights in test-time by moving it toward those vectors of the correctly predicted samples in a neighborhood of the test sample. We propose three R2-T2 strategies with different optimization objectives and neighbor-search spaces. R2-T2 consistently and significantly improves state-of-the-art LMMs' performance on challenging multimodal benchmarks of diverse tasks, without training any parameters in the base model. Our code can be accessed here.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **问题**：多模态大模型（LMMs）中，视觉等非语言模态的感知能力通常远弱于大语言模型（LLM）的推理能力，导致下游任务性能受限。尽管通过混合专家（MoE）替换单一视觉编码器可提供丰富、多粒度的表示，但MoE的路由器（router）是端到端训练的，对于每个测试样本不一定能产生最优的专家权重，造成次优选择。
- **意义**：设计一种无需重新训练模型即可在测试时动态优化路由权重的方法，有望弥合多模态感知与推理之间的鸿沟，提升模型泛化性和鲁棒性。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：基于假设“成功任务的知识和技能可迁移”，利用测试样本在参考集中正确预测的邻居样本的路由权重向量，通过局部优化调整测试样本的路由权重。
- **关键技术细节**：
  - 定义参考集：模型预测正确的样本及其路由权重组成的集合。
  - 邻居搜索：在任务嵌入空间（使用预训练嵌入模型如NV-Embed-V2）中基于kNN或ε-ball选择邻居。
- **三种策略**（算法流程文字说明）：
  - **邻域梯度下降（NGD）**：以邻居样本损失的加权平均作为代理目标，对当前路由权重进行一次或多次梯度下降更新。公式：\( \mathbf{r} \leftarrow \mathbf{r} - \lambda \nabla_{\mathbf{r}} \mathcal{L}(\mathbf{r}) \)，其中 \( \mathcal{L}(\mathbf{r}) = \frac{\sum_{i \in \mathcal{N}(x)} K(x_i,x) \ell(f(x_i,\mathbf{r}), y_i)}{\sum K} \)。
  - **核回归**：用核加权平均邻居路由权重得到估计 \( \hat{\mathbf{r}} \)，然后通过二分搜索在初始 \( \mathbf{r} \) 与 \( \hat{\mathbf{r}} \) 之间寻找最优插值系数 \( \alpha \) 以最小化代理损失。
  - **模式发现（Meanshift）**：在路由权重空间中对邻居应用密度估计，迭代地将当前权重移向局部密度最高的区域：\( \mathbf{r} \leftarrow \alpha \mathbf{r} + (1-\alpha)\bar{\mathbf{r}} \)，其中 \( \bar{\mathbf{r}} \) 是核加权平均。
- **优化终止条件**：固定步数（默认10步）或收敛。

## 3. 实验设计

- **使用的模型**：
  - **MoAI-7B**（6个专家：视觉专家IAUX、ILANG、ISELF；语言专家LAUX、LIMG、LSELF）
  - **MoVA-7B**（7个专家，包含SAM增强）
- **参考数据集与评估基准**（三类任务）：
  - 通用视觉理解：参考集 VQA-V2、Visual7W、CLEVR、COCO-QA；基准 MMBench、MME-P、CVBench 2D/3D、GQA
  - 知识推理：参考集 A-OKVQA、TQA、MathVista；基准 SQA-IMG、AI2D
  - OCR：参考集 ST-VQA、DocVQA；基准 TextVQA
  - （额外补充实验使用 MMMU、ChartQA、3DSRBench）
- **对比方法**：
  - 基座模型（base）
  - Oracle（使用真实标签作为上界）
  - R2-T2三种变体（NGD、Kernel Regression、Mode Finding）
  - 与多尺度SOTA VLMs（7B/8B/13B/34B）对比：InstructBLIP、Qwen-VL、mPLUG-Owl、ShareGPT4V、LLaVA-NeXT、Cambrian1、Mini-Gemini 等。
  - 额外基线：集成方法、带噪声路由、RAG和上下文学习等。

## 4. 资源与算力

- 文中未明确说明训练时长或GPU数量，但提供了以下信息：
  - **FLOPs分析**（Table 4）：基座模型每样本19.9 T FLOPs；R2-T2（NGD）67.5 T FLOPs；Oracle 11.8 T。
  - **延迟测量**（Table 16）：在RTX A6000上，基座模型平均7.8s/样本，R2-T2 25.6s（增加约3.3倍）。
  - 内存使用分析（Table 15）：基座模型 18GB，使用 NV-Embed-V2 时 27GB，使用轻量嵌入仅需20GB。
- **结论**：文中给出了计算开销的量化，但未提及具体训练或推理所使用的GPU数量及总时长。算力评估相对有限。

## 5. 实验数量与充分性

- **实验数量**：非常充分。
  - 主实验结果覆盖2个模型 × 8个基准 × 3种R2-T2策略 + 与11种SOTA模型对比。
  - 消融实验：邻居选择（kNN vs ε-ball）、核函数（4种）、嵌入模型（4种）、梯度步数（4种）、学习率调度（4种）。
  - 鲁棒性分析：参考集大小、任务覆盖不足、不匹配参考集、数据污染检查。
  - 额外基准：MMMU、ChartQA、3DSRBench。
  - 案例与专家转换分析：图、表、准确率转换统计。
- **充分性评估**：实验设计系统全面，消融覆盖关键超参数，对比方法多样（包括Oracle上界）。实验结果客观、公平，超参数固定（通过独立小实验确定），未针对每个基准过拟合。分析中还包括对参考集大小和匹配度的鲁棒性测试，增强了可信度。

## 6. 论文的主要结论与发现

- R2-T2在无需任何参数训练的情况下，显著提升多模态MoE模型在多种复杂基准上的性能，且可超越两倍参数规模的VLM。
- 邻域梯度下降（NGD）为三种策略中效果最优，能捕获70–80%的Oracle潜在提升。
- 路由权重优化可使模型从过度依赖单一专家（如ILANG）转向更均衡的专家分配，从而纠正大量错误预测（28.12%的初始错误被修正）。
- R2-T2对参考集质量敏感：任务相关参考集带来大幅提升，不匹配参考集增益极小；即使在稀疏覆盖场景下仍有改善。
- 计算开销适度增加（3.3倍延迟），但收益显著，且可通过轻量嵌入模型或自动化任务分类来降低。

## 7. 优点

- **训练免费**：无需微调基座模型参数，即插即用。
- **通用性强**：适用于多种多模态MoE架构，在不同任务类型和基准上一致提升。
- **方法新颖**：首次提出测试时路由重配问题，并设计了多种可行策略，为下游适应提供了新范式。
- **实验严谨**：包含大量消融、鲁棒性分析和数据污染检测，结论可靠；超参数通过独立数据集固定，避免过拟合。
- **分析深入**：通过专家转换可视化、准确率转换统计、案例研究等，清晰揭示了重路由如何修正错误。

## 8. 不足与局限

- **计算开销**：推理延迟增加约3.3倍，FLOPs提升显著，资源受限场景可能不适用。
- **依赖参考集**：需要预先构建高质量的正确预测参考集，且性能对参考集与测试样本的分布匹配敏感；在域外或极度稀缺任务上增益有限。
- **未探索端到端联合优化**：方法仅优化路由权重，未考虑同时调整专家内部参数或对齐模块。
- **模型覆盖面有限**：仅测试了7B规模的MoAI和MoVA，更大规模或纯文本MoE尚未验证。
- **自动化程度不足**：默认采用固定超参数（k=5, 10步等），未实现完全自适应调整；虽然尝试了自动化任务分类，但仍有少许下降。
- **实验覆盖偏差**：尽管基准多样，但缺少对视频、音频等更多模态的评估；部分基准（如MMMU、ChartQA）仅有单次实验，未报告方差。

（完）
