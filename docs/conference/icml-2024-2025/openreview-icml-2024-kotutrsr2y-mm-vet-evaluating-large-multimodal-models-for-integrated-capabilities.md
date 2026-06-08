---
title: "MM-Vet: Evaluating Large Multimodal Models for Integrated Capabilities"
title_zh: "MM-Vet: 评估大语言模型的集成能力"
authors: "Weihao Yu, Zhengyuan Yang, Linjie Li, Jianfeng Wang, Kevin Lin, Zicheng Liu, Xinchao Wang, Lijuan Wang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=KOTutrSR2y"
tags: ["query:multimodal"]
score: 8.0
evidence: 多模态集成能力评估基准
tldr: 该论文提出MM-Vet基准测试，用于评估大语言模型在复杂多模态任务上的集成能力。基准包含需要多种能力组合的问题，并设计了跨问答类型的评估指标。通过对多个模型测试，不仅给出性能排名，还提供了模型能力洞察，如不同任务上的强弱点分析。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 895, \"height\": 800, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 892, \"height\": 621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 772, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 648, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 436, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 561, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 386, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 571, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 292, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 838, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 520, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 703, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 712, \"height\": 478, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 480, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 684, \"height\": 478, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 635, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 711, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 490, \"height\": 632, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 565, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 573, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 572, \"height\": 388, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 538, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 456, \"height\": 316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 455, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 433, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 511, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 508, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 512, \"height\": 293, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 509, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 433, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 431, \"height\": 278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-kotutrsr2y/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 413, \"height\": 284, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-kotutrsr2y/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 830, \"height\": 518, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kotutrsr2y/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1769, \"height\": 601, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kotutrsr2y/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1725, \"height\": 289, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kotutrsr2y/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 828, \"height\": 205, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kotutrsr2y/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1781, \"height\": 96, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kotutrsr2y/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 705, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kotutrsr2y/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1123, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kotutrsr2y/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1402, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kotutrsr2y/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1725, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kotutrsr2y/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1219, \"height\": 2245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kotutrsr2y/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 876, \"height\": 518, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-kotutrsr2y/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 388, \"height\": 192, \"label\": \"Table\"}]"
motivation: 现有基准难以系统评估大语言模型在复杂多模态任务上的集成能力。
method: 设计包含多类复杂任务的MM-Vet基准，并开发跨类型评估指标。
result: 成功评估多个模型，揭示了它们在集成能力上的差异和模式。
conclusion: MM-Vet为多模态模型综合能力评估提供了有效工具和洞察。
---

## Abstract
We propose MM-Vet, an evaluation benchmark that examines large multimodal models (LMMs) on complicated multimodal tasks. Recent LMMs have shown various intriguing abilities, such as solving math problems written on the blackboard, reasoning about events and celebrities in news images, and explaining visual jokes. Rapid model advancements pose challenges to evaluation benchmark development. Problems include: (1) How to systematically structure and evaluate the complicated multimodal tasks; (2) How to design evaluation metrics that work well across question and answer types; and (3) How to give model insights beyond a simple performance ranking. To this end, we present MM-Vet, designed based on the insight that the intriguing ability to solve complicated tasks is often achieved by a generalist model being able to integrate different core vision-language (VL) capabilities. MM-Vet defines 6 core VL capabilities and examines the 16 integrations of interest derived from the capability combination. For evaluation metrics, we propose an LLM-based evaluator for open-ended outputs. The evaluator enables the evaluation across different question types and answer styles, resulting in a unified scoring metric. We evaluate representative LMMs on MM-Vet, providing insights into the capabilities of different LMM system paradigms and models.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：近年来，大型多模态模型（LMMs）展示了各种令人印象深刻的能力（如解答黑板上的数学题、推理新闻图像中的事件与名人、解释视觉笑话等）。然而，现有视觉语言基准（如 VQA v2、Text VQA、COCO Caption）通常只测试一两种核心能力（如识别、OCR），难以系统评估 LMMs 在复杂多模态任务上的综合表现。
- **核心问题**：如何系统化地构建和评估复杂多模态任务？如何设计跨问题类型和回答风格统一的评估指标？如何为模型提供超越简单排名的洞察？
- **整体含义**：复杂多模态任务的解构能力往往源于通用模型对多种核心视觉语言能力的集成。为此，作者提出 MM-Vet 基准，通过定义并测试 6 种核心能力及其 16 种组合，来全面评估 LMMs 的集成能力。

## 2. 方法论

### 核心思想
- 定义 6 种核心视觉语言（VL）能力：
  1. **Recognition**（识别）：场景、物体、属性、计数等。
  2. **OCR**（光学字符识别）：场景文本理解与推理。
  3. **Knowledge**（知识）：常识、百科、时事知识。
  4. **Language Generation**（语言生成）：流畅、信息丰富的文本输出。
  5. **Spatial Awareness**（空间意识）：物体与文本区域的空间关系理解。
  6. **Math**（数学）：算术运算能力。
- 从上述能力的组合中得到 **16 种感兴趣的集成任务**（如 Rec+Know+Gen、OCR+Spat+Math 等）。

### 数据构建
- 收集 187 张在线图像，搭配 205 个问题；额外从 VCR 选取 10 张、ChestX-ray14 选取 3 张，最终共计 **200 张图像、218 个样本**。
- 每个问题标注所需能力，并给出高质量真实答案（155 个人工标注，50 个从网络收集）。

### 评估指标：LLM-based Evaluator
- 提出使用 **GPT-4** 作为自动评分器，通过**少样本提示（few-shot prompt）** 为模型的开放输出（open-ended）打分，分数范围 0~1。
- 提示中包含不同答案风格（短答案、长答案、完全正确、部分正确、完全错误）的示例，使 LLM 能自动推断评分标准。
- 最终总分为所有样本分数的平均值（按能力或能力组合可分层计算）。

## 3. 实验设计

### 基准（Benchmark）
- **MM-Vet**：包含 218 个样本，覆盖 6 种核心能力及其 16 种集成，问题均为开放回答形式。

### 对比方法
- **端到端调优的 LMMs**：
  - OpenFlamingo-9B
  - BLIP-2-12B
  - LLaVA-7B / 13B（含多个变种：LLaMA-2、V1.3 336px 等）
  - MiniGPT-4-8B / 14B
  - LLaMA-Adapter v2-7B
  - Otter-9B
  - InstructBLIP-8B / 14B
- **LLM 工具使用方法**：
  - MM-ReAct（基于 GPT-3.5 / GPT-4）
  - Transformers Agent（GPT-4 作为 Agent）
- **闭源商业系统**（单独标记，避免不公平对比）：
  - GPT-4V（含 Turbo 变种）
  - Bard（Google）

### 评估设置
- 使用 GPT-4（0613）作为评估器，温度设为 0，对每个模型输出评估 5 次取平均。
- 报告每种能力和每个能力组合的分数，以及总分的均值和方差。

## 4. 资源与算力

- **论文未明确说明**训练或评估所使用的 GPU 型号、数量、训练时长等算力信息。
- 仅提到评估器使用 GPT-4（需 API 调用和付费），并指出开源模型（如 LLaVA、InstructBLIP）的预训练和微调过程使用了大规模数据集（如 LAION-400M、COYO-700M 等），但未给出具体 GPU 配置。
- 为方便非营利机构，作者托管了在线评估器（Huggingface Space）供免费使用。

## 5. 实验数量与充分性

### 主要实验
- 在 MM-Vet 上评估了 **11 种开源/半开源 LMMs** 和 2 种闭源系统，报告了每种能力和能力组合的分数（表 2、表 3）。
- 单独对 GPT-4V 进行详细分析（表 4、表 5），并附有成功/失败案例（附录图 3-6）。
- 与 Bard 进行了对比子集实验（168 样本，表 9、表 10）。

### 消融实验
- **评估器有效性验证**（表 6）：对比 10 种不同 LLM（LLaMA-2 系列、Mistral、Gemini Pro、Claude 3 Opus、GPT-3.5、GPT-4）作为评估器与人类评分的一致性（Δ）。结果显示 GPT-4 最佳（Δ=0.042）。
- **组合 LLM 评估器**（表 7）：尝试将 GPT-4 与其他 LLM 结合，发现并未改善，GPT-4 单独最好。
- **少样本示例消融**（表 8）：逐步增加提示中的示例数量，验证了使用全部 7 个示例效果最佳（Δ 最小）。

### 充分性评价
- 实验覆盖了当前主流 LMMs 的代表性架构和训练范式，对比较为全面。
- 消融实验聚焦于评估器设计，但对模型组件（如视觉编码器、语言模型、训练数据量）仅有定性讨论，缺乏系统消融（如控制变量更换视觉编码器、语言模型等）。因此实验充分性中等，但在评估方法验证上较为严谨。

## 6. 主要结论与发现

1. **整体排名**：
   - GPT-4V 总分最高（67.7%），远超其他方法。
   - MM-ReAct-GPT-4 第二（44.6%），表明工具增强的有效性。
   - 端到端模型中 LLaVA-13B（LLaMA-2）和 LLaVA-13B（V1.3, 336px）表现最好（约 32.5%~32.9%）。
2. **能力分析**：
   - **OCR、空间、数学**：工具使用方法（MM-ReAct）因集成外部工具而领先。
   - **识别、知识、语言生成**：端到端模型（如 LLaMA-Adapter v2、LLaVA）更强，受益于大规模预训练数据。
3. **模型设计洞察**：
   - 更强大的语言模型（如 LLaMA-2 相比 Vicuna）能显著提升多种能力。
   - 高分辨率图像输入（336px vs 224px）对空间意识和 OCR 有帮助。
   - 训练数据多样性和规模对识别和知识能力至关重要。
4. **评估器有效性**：GPT-4 作为评估器与人类评分高度一致（Δ=0.042），显著优于其他 LLM 和关键词匹配方法，为开放输出提供了可靠统一度量。

## 7. 优点

- **创新性**：
  - 首次从“能力集成”角度系统定义和评估 LMMs，揭示模型在复杂任务上的综合表现，而非单一技能。
  - 提出 LLM-based 评估器，统一了不同答案风格和问题类型，且易于扩展至更多输出形式（如框定位）。
- **实验设计**：
  - 评价指标既关注事实正确性也关注文本质量（通过少样本提示中的长答案示例）。
  - 提供按能力和按能力组合的细粒度分析，便于研究者识别模型强弱点。
- **开放性与可复现性**：
  - 代码、数据集和在线评估器均已公开托管（GitHub、Huggingface），降低了非营利机构的使用门槛。

## 8. 不足与局限

- **模态覆盖有限**：仅评估图像-文本输入输出，未涉及视频、音频、3D 等其他模态，限制了对通用多模态智能的全面评价。
- **数据规模较小**：MM-Vet 仅含 218 个样本，可能不足以代表真实世界的复杂多样性，且存在样本偏差风险（如部分来自互联网）。
- **评估器依赖 GPT-4**：目前只有 GPT-4 能较好匹配人类评分，导致评估成本较高（API 费用）；较弱 LLM 尚未达到同等可靠性。
- **消融实验不足**：未对模型组件（如视觉编码器类型、语言模型大小、训练数据组合）进行受控变量消融，对模型设计贡献的推断多基于现有模型比较，缺乏因果验证。
- **开放输出评估的模糊性**：虽然 LLM 评分器表现良好，但仍有评分方差（即使设置温度 0），且部分案例（如长文本摘要）评分可能存在歧义。
- **未涉及安全与偏见**：论文未讨论模型在回答中可能产生的不当内容或社会偏见等方面的评估。

（完）
