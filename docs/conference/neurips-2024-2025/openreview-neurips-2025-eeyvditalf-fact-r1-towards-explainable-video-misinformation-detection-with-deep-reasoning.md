---
title: "Fact-R1: Towards Explainable Video Misinformation Detection with Deep Reasoning"
title_zh: Fact-R1：面向可解释视频虚假信息检测的深度推理方法
authors: "Fanrui Zhang, Dian Li, Qiang Zhang, Chenjun, sinbadliu, Junxiong Lin, Jiahong Yan, Jiawei Liu, Zheng-Jun Zha"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=EeyvDitalf"
tags: ["query:mm-cot"]
score: 9.0
evidence: 基于长链推理的视频虚假信息检测
tldr: 多模态虚假信息检测缺乏大规模数据集和深度推理能力。本文构建了包含10万视频-文本对的FakeVV基准，并提出Fact-R1框架，通过长链思维指令微调、偏好对齐和基于规则的强化学习三阶段训练，使模型能生成可解释的推理链。实验表明，Fact-R1在多种场景下显著优于现有方法，并提供了可理解的错误分析。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1428, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1159, \"height\": 336, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1407, \"height\": 816, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1392, \"height\": 783, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 539, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 577, \"height\": 271, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1362, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1416, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1408, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1404, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1439, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1044, \"height\": 1038, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1048, \"height\": 939, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 573, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 587, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 577, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 587, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1273, \"height\": 812, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1274, \"height\": 810, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1275, \"height\": 800, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1272, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1272, \"height\": 799, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eeyvditalf/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1287, \"height\": 1149, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-eeyvditalf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eeyvditalf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 596, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eeyvditalf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 459, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eeyvditalf/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 491, \"height\": 238, \"label\": \"Table\"}]"
motivation: 现有视频虚假信息检测方法缺乏深度推理能力，且多模态数据集规模有限。
method: 提出Fact-R1框架，包含长链CoT指令微调、偏好对齐和协作规则强化学习三阶段训练，利用推理链增强可解释性。
result: "在FakeVV基准上，Fact-R1检测准确率超过基线12%，且生成的推理链有效辅助人类判断。"
conclusion: 将长链CoT引入多模态虚假信息检测，显著提升了模型的推理能力和可解释性。
---

## Abstract
The rapid spread of multimodal misinformation on social media has raised growing concerns, while research on video misinformation detection remains limited due to the lack of large-scale, diverse datasets. Existing methods often overfit to rigid templates and lack deep reasoning over deceptive content. To address these challenges, we introduce FakeVV, a large-scale benchmark comprising over 100,000 video-text pairs with fine-grained, interpretable annotations. In addition, we further propose Fact-R1, a novel framework that integrates deep reasoning with collaborative rule-based reinforcement learning. Fact-R1 is trained through a three-stage process: (1) misinformation long-Chain-of-Thought (CoT) instruction tuning, (2) preference alignment via Direct Preference Optimization (DPO), and (3) Group Relative Policy Optimization (GRPO) using a novel verifiable reward function. This enables Fact-R1 to exhibit emergent reasoning behaviors comparable to those observed in advanced text-based reinforcement learning systems, but in the more complex multimodal misinformation setting. Our work establishes a new paradigm for misinformation detection, bridging large-scale video understanding, reasoning-guided alignment, and interpretable verification.

---

## 论文详细总结（自动生成）

# 论文总结：Fact-R1: Towards Explainable Video Misinformation Detection with Deep Reasoning

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：社交媒体上多模态虚假信息（尤其是短视频）迅速传播，手动事实核查难以应对，自动化检测变得迫切。现有方法主要集中于图像-文本模态，视频模态因数据收集和标注困难，研究受限。
- **主要挑战**：
  - 现有视频数据集规模小、主题单一、时间跨度窄，缺乏细粒度标注和可解释性标准。
  - 已有方法容易过拟合于模板化模式，缺乏对欺骗性内容的深度推理能力。
  - 利用真实视频搭配虚假叙事（Out-of-Context，OOC）的手法日益普遍，但模型难以有效检测。
- **研究目标**：构建大规模、多样化、可解释的视频虚假信息基准数据集，并提出一种融合深度推理与强化学习的检测框架，实现可解释的检测。

## 2. 方法论：核心思想、关键技术细节、公式或算法流程

### 整体框架：Fact-R1

Fact-R1 是基于多模态大语言模型（MLLM）的三阶段训练框架，将深度推理与基于规则的协作式强化学习相结合。

#### 2.1 第一阶段：Misinformation Long-CoT Instruction Tuning

- **目的**：为模型注入领域特定的推理知识和长链思维（Long Chain-of-Thought）能力。
- **数据构建**：利用 DeepSeek-R1，基于生成的新闻视频字幕、音频转录和标题，生成包含 `<think>` 标签的多步推理轨迹。仅保留标签正确且推理中准确识别操纵实体的样本，得到约 85K 高质量实例。
- **训练**：冻结视觉编码器，对 Qwen2.5-VL 使用 LoRA（r=128, α=256）进行指令微调，学习率 LoRA 部分 2×10⁻⁵，多模态投影仪 2×10⁻⁶，batch size 2，训练 2 轮，优化器 AdamW。

#### 2.2 第二阶段：Preference Alignment via DPO

- **目的**：对齐模型输出与人类期望，减少幻觉、错误实体归因和格式不一致。
- **数据**：5K 对人工标注的偏好数据，每对包含偏好输出（准确、连贯）和次优输出。
- **训练**：使用 Direct Preference Optimization（DPO）目标函数，无需显式奖励模型。损失为：
  $$
  \mathcal{L}_{\text{DPO}} = -\log \frac{\exp(\beta \cdot r(y_{\text{label}}))}{\exp(\beta \cdot r(y_{\text{label}})) + \exp(\beta \cdot r(y_{\text{pred}}))}
  $$
  其中 \(r(y)\) 是当前策略与冻结参考策略之间的对数似然比。训练 1 轮，batch size 4，学习率 2×10⁻⁵，β=0.1，梯度裁剪 1.0。

#### 2.3 第三阶段：GRPO with Verifiable Reward Function

- **目的**：通过仅基于奖励的自演化训练，使模型自主提升推理能力。
- **方法**：采用 Group Relative Policy Optimization（GRPO），对每个输入采样 G 个候选响应，计算奖励并归一化得到优势值：
  $$
  A_i = \frac{r_i - \mu}{\sigma}
  $$
  策略优化损失为：
  $$
  \mathcal{L}_{\text{GRPO}} = \frac{1}{G}\sum_{i=1}^G \left[ \min\left( \frac{\pi_\theta(y_i)}{\pi_{\text{old}}(y_i)} A_i, \operatorname{clip}\left(\frac{\pi_\theta(y_i)}{\pi_{\text{old}}(y_i)}, 1-\epsilon, 1+\epsilon\right) A_i\right) - \beta D_{\text{KL}}(\pi_\theta \| \pi_{\text{ref}}) \right]
  $$
- **可验证奖励函数**：由四个部分组成：
  - **Accuracy Reward** (\(R_{\text{acc}}\))：预测标签与真实标签是否一致。
  - **Format Reward** (\(R_{\text{format}}\))：推理是否在正确标签内。
  - **Reasoning Keywords Reward** (\(R_{\text{word}}\))：推理轨迹是否包含“First”、“However”、“In conclusion”等关键反思词。
  - **Entity Grounding Reward** (\(R_{\text{entity}}\))：对于假样本，使用法官模型判断推理中是否准确指认了被操控的实体。
  
  最终总体奖励：
  - 若真实标签为 real：\(R = 0.8R_{\text{acc}} + 0.1R_{\text{format}} + 0.1R_{\text{word}}\)
  - 若真实标签为 fake：\(R = 0.7R_{\text{acc}} + 0.1R_{\text{format}} + 0.1R_{\text{word}} + 0.1R_{\text{entity}}\)

- **辅助任务**：同时引入新闻图片 OCR 和新闻视频字幕两个辅助任务，以增强视觉-文本对齐，奖励函数包含准确率（OCR 用归一化编辑距离，字幕用 ROUGE-L）和格式奖勋。

- **GRPO 训练细节**：172 steps，每个输入采样 5 个候选响应，学习率 1×10⁻⁶。训练数据包括主任务的 15K 样本和辅助任务的 5K 样本。

### 数据集 FakeVV 构建

- **数据收集**：从 BBC News、Guardian News、CNN、The New York Times 四个官方新闻频道收集 2006.11–2025.02 间 12 万原始视频，经清洗（去除非新闻、超 5 分钟、近重复事件）后得到 10 万高质量视频-文本对。
- **字幕生成**：使用 GPT-4o 基于关键帧、视觉实体和标题生成新闻领域视频字幕。
- **虚假样本构造**：采用非随机实体替换策略，通过 CLIP 相似性检索，对人物、地点、事件、组织四种实体进行替换，生成 10.2 万伪造样本，并标注被操控实体和类型。数据集分为 10 万训练样本（2025 年前）和 2000 测试样本（2025 年），各占 50% 真实/虚假，无显著单模态文本偏差。

## 3. 实验设计：数据集、Benchmark 与对比方法

### 数据集

- **FakeVV**：本文提出的 10 万级数据集，测试集 2000 样本（2025 年），涵盖四种操控类型，提供可解释性标注。
- **FakeSV**：中文短视频虚假新闻数据集，含社交上下文（评论、发布者元数据），视频标题翻译为英文。时间划分：70% 训练、15% 验证、15% 测试。
- **FakeTT**：英文 TikTok 平台虚假新闻数据集，同样按时间分割。

### 评估指标

Accuracy（ACC）、Precision、Recall、F1 Score。

### 基线方法

共 15 个基线，分为四组：

1. **单模态**：BERT（仅文本）。
2. **多模态专用方法**：TikTec、FANVM、SV-FEND、FakingRec。
3. **闭源 MLLMs**：Gemini2-thinking、GPT-4o、GPT-o1-mini、DeepSeek-R1（纯文本）。
4. **开源 MLLMs**：Qwen2.5-VL-7B、Qwen2.5-VL-72B、QVQ-72B-preview、InternVL2.5-8B、InternVL2.5-78B-MPO。

前两组在 FakeVV 训练集上训练；后两组零样本评估。对于不支持视频的模型（如 DeepSeek-R1、GPT-o1-mini），使用新闻领域视频字幕作为文本替代。

## 4. 资源与算力

- 所有实验在 **8×NVIDIA A100 GPU** 上使用 PyTorch 进行。
- 基础 MLLM 为 Qwen2.5-VL，默认 8 帧采样。
- 第一阶段训练 2 轮；第二阶段训练 1 轮（5K 偏好对）；第三阶段训练 172 steps。
- 文中未明确给出具体训练时长和总计算量，但提供了详细的超参数设置。

## 5. 实验数量与充分性

- **主要对比实验**：在三个数据集（FakeSV、FakeTT、FakeVV）上比较 Fact-R1 与 15 个基线，报告 ACC、Prec、Rec、F1。
- **消融实验**：
  - 三个训练阶段的贡献：w/o SFT、w/o DPO、w/o GRPO（表 3）。
  - 奖励函数与辅助任务的影响：w/o Keywords、w/o Entity、w/o Ocr、w/o Caption（表 4）。
- **可解释性分析**：对 6 个模型（包括 Fact-R1）评估其推理轨迹中正确识别被操控实体的准确率（图 5），并按操控类型细分（图 6）。
- **GRPO 训练曲线**：奖励和响应长度随训练步数的变化（图 14、15）。
- **法官模型一致性分析**：比较 GPT-4o-mini 与其他模型与人类评估的一致性（图 16、17）。
- **案例研究**：展示了成功推理、多模态信号贡献、失败案例、真实新闻正确分类、真实世界虚假新闻检测等。
- **充分性**：实验覆盖三个数据集、多种基线和消融，评估了检测性能和可解释性，客观公正。但未公开统计显著性检验（如 error bars），仅报告单一运行结果。

## 6. 主要结论与发现

- **检测性能**：Fact-R1 在所有三个数据集上均取得最佳平均 ACC 和 F1，尤其在 FakeVV 上 ACC 达 81.2%，F1 达 80.3%，显著超越所有基线（包括 GPT-4o、DeepSeek-R1 等）。
- **可解释性**：Fact-R1 在正确预测的前提下，对被操控实体的识别准确率最高（76.4%），远超其他模型（最高 67.3%），表明其推理链能准确指出误导来源。
- **三阶段训练必要性**：移除任一阶段均导致性能下降，证实长 CoT 指令微调、DPO 偏好对齐、GRPO 强化学习逐步构建推理能力。
- **奖励函数组件贡献**：移除关键词奖励、实体奖励或辅助任务（OCR/字幕）均会降低性能，证明这些组件对推理和检测都很重要。
- **多模态信号价值**：音频中的关键实体（如“Chancellor”）和图像 OCR 文本（如“Trump”）能提供关键线索，帮助模型做出正确判断。
- **局限性**：当音频和 OCR 均无法提供有效线索时，模型在实体指认上容易失败；数据集仅来自四个西方新闻机构，存在地理文化偏差。

## 7. 优点

- **大规模高质量数据集**：FakeVV 是当前最大的视频虚假新闻数据集，10 万样本，覆盖 2006–2025 年，包含细粒度的被操控实体标注和操控类型，支持可解释性评估。
- **创新的非随机实体替换策略**：通过 CLIP 相似性检索和 GPT-4o 改写，生成语义一致但事实矛盾的虚假样本，避免模型过拟合于表面模式。
- **三阶段训练框架**：开创性地将长链思维指令微调、偏好对齐和基于规则的强化学习结合用于视频虚假信息检测，具有范式意义。
- **可验证奖励函数**：专门针对虚假信息检测设计，包含准确率、格式、关键词和实体指认四个维度，并引入辅助任务增强视觉-文本对齐，使模型能进行结构化、可解释的推理。
- **全面的实验验证**：在三个数据集上与 15 种基线对比，进行充分的消融和可解释性分析，结果具有说服力。
- **开源有望**：论文提供了代码和数据集（仅供学术研究），有助于推动领域发展。

## 8. 不足与局限

- **检测准确率仍有限**：在真实场景中，由于视频内容复杂、事实主张模糊、误导策略不断演进，检测准确率总体偏低，模型泛化性和鲁棒性需进一步提升。
- **可解释性失败案例**：部分样本虽预测正确，但推理轨迹中未准确识别被操控实体，说明模型在缺乏交叉模态线索时推理能力受限。
- **数据集偏差**：仅从四个西方新闻机构（BBC、Guardian、CNN、NYT）收集，导致地理和文化偏差，对其他地区和语境的泛化性存疑。
- **计算资源昂贵**：三阶段训练（尤其 GRPO）需要 8×A100 GPU，对资源受限的研究机构不友好。
- **潜在负面社会影响**：错误预测（尤其是带有看似合理但事实错误的推理）可能误导用户或压制合法言论；过度依赖自动系统可能削弱人工监督。
- **未提供统计显著性检验**：实验仅报告单次运行结果，未给出误差棒或置信区间，结果的稳定性需进一步确认。
- **未讨论模型对对抗攻击的鲁棒性**：恶意用户可能故意构造对抗样本绕过检测，本文未涉及这一重要方面。

（完）
