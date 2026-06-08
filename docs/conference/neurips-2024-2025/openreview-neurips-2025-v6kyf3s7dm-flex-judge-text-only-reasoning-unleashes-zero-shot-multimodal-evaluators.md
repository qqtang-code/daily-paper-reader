---
title: "Flex-Judge: Text-Only Reasoning Unleashes Zero-Shot Multimodal Evaluators"
title_zh: Flex-Judge：文本推理释放零样本多模态评估器
authors: "Jongwoo Ko, Sungnyun Kim, Sungwoo Cho, Se-Young Yun"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=v6kyF3S7dM"
tags: ["query:mm-cot"]
score: 4.0
evidence: 基于推理引导的多模态评估器
tldr: 多模态评估器通常需要大量模态特定训练数据，泛化性差。本文提出Flex-Judge，利用结构化文本推理作为通用决策模式，仅需少量文本推理数据即可零样本泛化至多种多模态评估任务。尽管方法涉及推理，但其主要贡献在于评估而非多步推理本身。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1430, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1430, \"height\": 511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1399, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 802, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 575, \"height\": 281, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1439, \"height\": 299, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1442, \"height\": 993, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1432, \"height\": 1280, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1431, \"height\": 1286, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1439, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1435, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1433, \"height\": 855, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1429, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 343, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 342, \"height\": 344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 345, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1425, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1424, \"height\": 583, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-v6kyf3s7dm/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1443, \"height\": 1248, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 660, \"height\": 377, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 1106, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 769, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 737, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1453, \"height\": 353, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 831, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 617, \"height\": 330, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 758, \"height\": 190, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1444, \"height\": 387, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1444, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1440, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1449, \"height\": 332, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 580, \"height\": 155, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-v6kyf3s7dm/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1452, \"height\": 489, \"label\": \"Table\"}]"
motivation: 多模态评估器依赖大量模态特定数据，难以泛化至新任务。
method: 提出Flex-Judge，通过微调LLM对结构化文本推理进行学习，将其作为通用评估范式，无需模态特定训练。
result: 在多种多模态评估任务上，Flex-Judge零样本性能接近甚至超过有监督基线，且跨模态泛化能力强。
conclusion: 文本推理可作为多模态评估的有效中间表示，极大降低数据收集成本。
---

## Abstract
Human-generated reward signals are critical for aligning generative models with human preferences, guiding both training and inference-time evaluations. While large language models (LLMs) employed as proxy evaluators, i.e., LLM-as-a-Judge, significantly reduce the costs associated with manual annotations, they typically require extensive modality-specific training data and fail to generalize well across diverse multimodal tasks. In this paper, we propose **Flex-Judge**, a reasoning-guided multimodal judge model that leverages minimal textual reasoning data to robustly generalize across multiple modalities and evaluation formats. Our core intuition is that structured textual reasoning explanations inherently encode generalizable decision-making patterns, enabling an effective transfer to multimodal judgments, e.g., with images or videos. Empirical results demonstrate that Flex-Judge, despite being trained on significantly fewer text data, achieves competitive or superior performance compared to state-of-the-art commercial APIs and extensively trained multimodal evaluators. Notably, Flex-Judge presents broad impact in modalities like molecule, where comprehensive evaluation benchmarks are scarce, underscoring its practical value in resource-constrained domains. Our framework highlights reasoning-based text supervision as a powerful, cost-effective alternative to traditional annotation-intensive approaches, substantially advancing scalable multimodal model-as-a-judge.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与整体含义（研究动机与背景）
- **问题**：现有大规模多模态评估器（如LLM-as-a-Judge）通常需要大量模态特定的训练数据（如图像-文本偏好对），且泛化能力差，难以扩展到新模态（如音频、分子）。商用API虽然强大但存在透明度、可控性及成本问题，且底层模型更新可能导致评估质量下降。
- **动机**：作者提出假设——结构化的文本推理解释本身编码了可泛化的决策模式，因此仅通过小规模高质量的文本推理数据训练，即可使多模态大语言模型（MLLM）获得跨模态的零样本评估能力。
- **含义**：该工作挑战了“大规模模态特定数据是训练有效多模态评估器必要条件”的传统观点，为低成本、可扩展的多模态评估提供了新范式。

### 2. 方法论：核心思想、关键技术细节、算法流程
- **核心思想**：**推理引导的跨模态泛化**。使用一个预训练的推理型评估模型（JudgeLRM-7B）生成高质量的文本推理数据（包含 ` <think>` `</think>` 标签的结构化推理链），然后仅用此文本数据微调通用MLLM（如Qwen2.5-VL-7B或Qwen2.5-Omni-7B），得到Flex-Judge。微调后模型能直接用于图像、视频、音频、分子等模态的评估任务，无需任何模态特定的数据。
- **关键技术细节**：
  - **数据策展**：从JudgeLM-100K数据集中利用JudgeLRM-7B采样推理式评估响应，通过质量（与GPT-4o评分一致）、长度（越长的推理链代表高难度样本）、格式多样性（单分制、成对比较、批量排名）和温度（低温采样保持on-policy）等维度筛选出约1K条高质量文本推理数据。
  - **模型训练**：仅微调MLLM的语言模型部分（如Qwen2.5-VL-7B），冻结视觉/音频编码器等模态特定模块。使用标准的有监督微调（SFT）方式，学习生成“先推理后回答”的结构化输出。
  - **推理**：在推理阶段，Flex-Judge通过生成带推理链的答案来执行评估。支持多数投票或预算强制（budget forcing）等推理时扩展技术以提升性能。
- **算法流程**：输入任务（如图像+问题）→ MLLM编码多模态输入 → 基于文本推理知识生成 ` <think>` 评估理由 → 输出 ` <answer>` 评分或偏好。

### 3. 实验设计：数据集、Benchmark、对比方法
- **数据集与Benchmark**：
  - **图像理解**：MLLM-as-a-Judge（14个视觉-语言子任务）、**VL-RewardBench**（复杂推理与幻觉检测）。
  - **图像生成**：**MJ-Bench**（对齐、安全、伪影）、**GenAI-Bench**（图像生成/编辑/视频生成）。
  - **音频质量**：**NISQA**、**BVCC**、**SOMOS**（MOS预测）、**VoxSim**（说话人相似度）。
  - **分子领域**：**PAMPA渗透性预测**（Mol-LLaMA+Flex-Mol-LLaMA评估）。
  - 额外基准：**Multimodal RewardBench**、**JudgeAnything**（任意-任意模态）。
- **对比方法**：
  - 商业API：GPT-4V、GPT-4o、Gemini全系列、Claude 3 Opus。
  - 开源有监督评估器：LLaVA-Critic-7B、Prometheus-Vision-13B（均需>100K多模态数据）。
  - 训练无关（TF）基线：Qwen2.5-Omni-7B、Qwen2.5-VL-7B、LLaVA-1.6-34B等。
  - 专用模型：PickScore-v1、HPS-v2.1、ImageReward（图像偏好模型）。
  - 分子领域基线：Mol-LLaMA、Mol-Instructions、3D-MoLM、LLaMo。

### 4. 资源与算力
- **明确说明**：训练Flex-Judge（7B）使用 **2块NVIDIA A6000 GPU**，每轮训练约 **1.5小时**（1个epoch）。总计算开销极低，体现了论文强调的“成本高效”。
- **评注**：论文未详细说明消融实验或推理时扩展的总GPU小时数，但训练资源清晰且经济。

### 5. 实验数量与充分性
- **大量实验**：包含图像理解2大基准（MLLM-as-a-Judge含14子任务、VL-RewardBench含3个方面）、图像生成2个基准（MJ-Bench含3个方面、GenAI-Bench含3个任务）、音频4个数据集、分子两个任务（Best-of-N、DPO），以及2个额外综合基准（Multimodal RewardBench、JudgeAnything）。此外还有10余组消融实验（推理影响、数据量、温度、模型大小、位置/长度偏差分析、推理时缩放等）。
- **充分性评估**：实验覆盖范围广、对比基线全面（商业与开源均有）、评价指标多样（Pearson相关系数、准确率、Levenshtein距离、LCC、SRCC等）。消融实验验证了推理链、数据质量、格式多样性等关键设计。整体上实验设计客观、公平（如采用随机顺序、多次采样、tie选项等去偏方法）。

### 6. 主要结论与发现
- Flex-Judge仅使用 **1K文本推理数据**，在图像、视频、音频、分子等多个模态的评估任务上，性能 **匹配甚至超越** 需要大规模多模态数据训练的评估器和部分商业API。
- 核心发现：**文本推理是通用评估模式**，能够零样本迁移到其他模态，无需模态特定训练。
- 推理时扩展（多数投票、预算强制）能进一步提升Flex-Judge性能，且效果优于非推理型基线。
- 在分子领域（PAMPA任务），Flex-Judge作为奖励模型用于Best-of-N采样和DPO训练，使Mol-LLaMA准确率达到 **80.10%**，超越此前最佳方法。

### 7. 优点
- **数据效率极高**：仅1K文本推理数据即可获得强泛化能力，大幅降低标注和数据收集成本。
- **跨模态零样本**：无需针对新模态收集偏好数据，即可用于图像、视频、音频、分子等任务，特别适合数据稀缺领域。
- **推理透明**：模型输出结构化推理过程，可解释性强，有助于诊断错误。
- **训练简单、资源需求低**：仅需微调LLM部分2小时，对比动辄需要上百GB GPU内存的基线方法，实用性突出。
- **鲁棒性**：通过质量筛选、格式多样化、低温on-policy采样等手段，有效防止灾难性遗忘，保持多模态编码能力。

### 8. 不足与局限
- **依赖LLM的推理能力**：方法要求底层MLLM本身具备较强文本推理能力（如Qwen2.5-VL），对于弱推理的MLLM（如基于Flan-T5-XL的3D-LLM）不适用（论文坦诚指出）。这限制了框架在推理能力不足的骨干模型上的推广。
- **模型规模限制**：仅测试了3B和7B模型，更大规模（如72B）的Flex-Judge效果更好，但实验只部分覆盖（表9有32B LoRA），未全面研究规模扩展规律。
- **某些任务上仍低于SOTA**：在音频MOS/SS任务上，Flex-Judge虽优于训练无关基线，但仍滞后于任务特定微调模型（如Qwen2-Audio fine-tuned）。这提出了“零样本”与“专业微调”之间的权衡。
- **位置偏差**：模型存在一定位置偏好（倾向于第一个回答），论文通过随机顺序处理但未彻底消除，可能影响公平性。
- **分子实验范围有限**：仅针对PAMPA单一任务评估，未在更多分子理解任务（如反应预测、分子属性预测）上验证，泛化性需进一步检验。

（完）
