---
title: "ThinkSound: Chain-of-Thought Reasoning in Multimodal LLMs for Audio Generation and Editing"
title_zh: ThinkSound：多模态大模型中的链式推理用于音频生成与编辑
authors: "Huadai Liu, Kaicheng Luo, Jialei Wang, Wen Wang, Qian Chen, Zhou Zhao, Wei Xue"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=mj8VN4MyrO"
tags: ["query:mm-cot"]
score: 8.0
evidence: 在音频生成中进行多模态逐步推理
tldr: 视频到音频生成需要理解视觉动态和空间关系，现有端到端方法缺乏显式推理。论文提出ThinkSound，将生成过程分解为三个阶段：基础音效生成、物体级精化、时空调整，每一步都基于链式推理。该方法实现了交互式音频编辑，生成音频更贴合视频内容，展示了链式推理在多模态生成中的潜力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-mj8vn4myro/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 709, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mj8vn4myro/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1353, \"height\": 778, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mj8vn4myro/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mj8vn4myro/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1275, \"height\": 980, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mj8vn4myro/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1333, \"height\": 723, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 379, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 769, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 778, \"height\": 211, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 796, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 735, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 760, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1193, \"height\": 449, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1332, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1083, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1098, \"height\": 220, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1128, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1257, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1260, \"height\": 182, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mj8vn4myro/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1246, \"height\": 223, \"label\": \"Table\"}]"
motivation: 视频到音频生成需要复杂的多模态推理，现有方法难以捕捉细节因果关系。
method: 将生成过程分解为三个阶段，各阶段通过链式推理逐步优化。
result: 生成的音频在语义一致性和时间同步性上优于端到端方法，支持交互式编辑。
conclusion: 链式推理能有效提升多模态生成任务的可控性和质量。
---

## Abstract
While end-to-end video-to-audio generation has greatly improved, producing high-fidelity audio that authentically captures the nuances of visual content remains challenging. Like professionals in the creative industries, this generation requires sophisticated reasoning about items such as visual dynamics, acoustic environments, and temporal relationships. We present **ThinkSound**, a novel framework that leverages Chain-of-Thought (CoT) reasoning to enable stepwise, interactive audio generation and editing for videos. Our approach decomposes the process into three complementary stages: foundational foley generation that creates semantically coherent soundscapes, interactive object-centric refinement through precise user interactions, and targeted editing guided by natural language instructions. At each stage, a multimodal large language model generates contextually aligned CoT reasoning that guides a unified audio foundation model. Furthermore, we introduce **AudioCoT**, a comprehensive dataset with structured reasoning annotations that establishes connections between visual content, textual descriptions, and sound synthesis.  Experiments demonstrate that ThinkSound achieves state-of-the-art performance in video-to-audio generation across both audio metrics and CoT metrics, and excels in the out-of-distribution Movie Gen Audio benchmark. The project page is available at https://ThinkSound-Project.github.io.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：视频到音频（V2A）生成需要理解复杂的视觉动态、声学环境和时序关系，例如判断猫头鹰何时鸣叫、何时振翅，以及树梢摇曳产生的细微声音。现有端到端方法（如Diff-Foley、FoleyGen、MMAudio等）往往生成通用声音或无法精确同步到视觉线索，缺乏显式推理和用户交互能力。
- **整体含义**：本文旨在将复杂音效设计分解为可解释的逐步推理过程，让多模态大语言模型（MLLM）通过链式推理（CoT）引导音频生成，从而提升可控制性、上下文一致性和音频质量。

## 2. 论文提出的方法论

- **核心思想**：使用CoT推理将视频音频生成分解为三个直观且可交互的阶段，每个阶段由微调后的MLLM（VideoLLaMA2）生成结构化推理链，进而引导统一的音频基础模型（基于流匹配的MM-DiT架构）合成高质量音频。
- **关键技术细节**：
  1. **三个阶段**：
     - **Stage 1：基础Foley生成** — 分析整个视频，生成语义与时间匹配的背景声音场景。
     - **Stage 2：交互式对象中心细化** — 用户点击视频中特定对象（通过Grounded SAM-2获取ROI），模型生成针对该对象的音频推理，并融合到现有音轨中。
     - **Stage 3：基于自然语言指令的目标编辑** — 用户提供高级编辑指令（如添加、移除、修补、延长音频），模型通过CoT推理执行精准操作。
  2. **CoT推理模块**：基于VideoLLaMA2微调，训练目标为下一个token预测的交叉熵损失。训练数据为自建的AudioCoT数据集，使模型获得音频理解、结构化分解和多模态指令跟随能力。
  3. **统一音频基础模型**：
     - 使用预训练VAE将音频编码为潜在表示，采用条件流匹配（conditional flow matching）训练速度场预测。
     - 多模态条件：视频（通过MetaCLIP编码）、CoT文本（通过T5编码）、音频上下文。
     - 架构：增强的MM-DiT，包含多流Transformer块（不同模态独立处理但共享注意力）和单流Transformer块，通过门控机制融合视频与音频特征，全局条件通过AdaLN注入。
     - 训练时采用CFG dropout（每个模态以0.2概率丢弃），支持推理时任意模态组合。
- **数据集**：构建AudioCoT数据集，包含约2531小时音频-视频/音频-文本对，来自VGGSound、AudioSet、Freesound、AudioCaps、BBC Sound Effects，通过多阶段自动管道生成CoT注释（使用VideoLLaMA2、Qwen2-Audio、GPT-4.1-nano），并经过质量筛选（CLAP分数、对象跟踪一致性、人工审核）。

## 3. 实验设计

- **数据集与评测基准**：
  - 视频-音频生成（Stage 1）：VGGSound 测试集（区内）和 MovieGen Audio Bench（区外）。
  - 对象焦点生成（Stage 2）：AudioCoT 测试集。
  - 音频编辑（Stage 3）：AudioCoT 测试集。
  - 难度分层：根据语义一致性、时间同步、声景复杂度将VGGSound样本分为易/中/难三级。
- **对比方法**：See&Hear、V-AURA、FoleyCrafter、Frieren、V2A-Mapper、MMAudio（Stage 1）；MMAudio（Stage 2）；AudioLDM-2、Edit Friendly DDPM（Stage 3）。所有对比均使用官方代码或作者提供样本。
- **评估指标**：
  - 客观：Fréchet Distance (FD, OpenL3空间)、KL散度（PaSST和PaNNs模型）、DeSync（Synchformer模型）、CLAP分数（对caption和CoT）。
  - 主观：Mean Opinion Score (MOS-Q 音频质量，MOS-A 语义与时间对齐)，由15名受过训练的评估员在5分制上打分。

## 4. 资源与算力

- **VAE 训练**：初始化自Stability AI的预训练权重，混合精度训练，batch size=144，24块A800 GPU，500,000步。之后冻结编码器，训练解码器（mask ratio=0.1）额外500,000步。优化器：AdamW，生成器lr=3e-5，判别器lr=6e-5。
- **基础模型训练**：EMA + 自动混合精度，8块A100 GPU，有效batch size=256，100,000步，lr=1e-4，CFG dropout=0.2每模态。
- **任务微调**：类似设置，8块A100 GPU，50,000步，有效batch size=256，lr=1e-4。
- **总参数量**：1.3B（Large版本）。

## 5. 实验数量与充分性

- **实验数量**：共14个表格和2个图例，涵盖：
  - 主对比（表1, 表2, 表3, 表4）
  - 消融实验（表5: 文本编码策略；表6: 多模态融合机制；表9: 模型大小；表10: 难度等级；表11: 粗粒度vs细粒度CoT；表12: CoT结构重要性；表13: CoT冗长度；表14: MLLM推理质量评估）
  - 定性分析（图4，语谱图对比）
- **充分性与公平性**：实验覆盖主要任务、多种基线、多角度消融，主观评估采用标准化MOS流程。公平性方面，基线方法通过官方代码复现或作者提供样本，指标计算一致。但CLAP分数存在局限（原始VGGSound caption质量低），作者引入CLAP CoT作为补充。未报告误差条，但主观MOS给出了方差。整体充分且客观。

## 6. 主要结论与发现

- ThinkSound在VGGSound测试集上所有主观指标和大部分客观指标上达到SOTA（如FD 34.56 vs MMAudio 43.26；MOS-Q 4.02 vs 3.84；MOS-A 4.18 vs 3.97）。
- CoT推理是关键：移除CoT后，CLAP CoT 从0.46下降至0.41，其他指标亦恶化（表1）。
- 在区外的MovieGen Audio Bench上仍保持最佳（表2）。
- 对象焦点生成和音频编辑任务中均优于对比方法（表3、表4）。
- 消融表明：CLIP+T5双编码优于单一编码；门控融合优于线性加和；精细CoT优于粗糙CoT；有序CoT优于随机或仅关键词；适度简洁的CoT优于过度详细。
- 模型规模越大性能越好（Large>Medium>Small）。

## 7. 优点

- **方法创新**：首次将CoT推理系统性融入视频音频生成，分解为三步交互流程，兼顾全局一致性、对象级控制和文字级编辑，可解释性强。
- **统一架构**：单个基础模型支持任意模态组合输入，通过CFG dropout实现灵活推理，无需多个专用模型。
- **数据集贡献**：AudioCoT提供大规模结构化CoT注释，填补了推理导向音频生成数据的空白。
- **实验全面深入**：多维度消融验证设计选择，并覆盖不同难度、模型大小、CoT粒度等。
- **用户交互友好**：点击+自然语言指令，降低专业门槛。

## 8. 不足与局限

- **时空理解精度有限**：当前MLLM在准确定位声音时间戳和精细空间位置方面仍有不足，可能影响时序对齐。
- **数据多样性不足**：开源视频-音频数据集的覆盖有限（如缺少罕见或文化特定声音事件），可能导致模型泛化偏差。
- **潜在负面社会影响**：可被用于生成虚假音频（deepfake），且训练数据若存在偏差会被放大。
- **计算资源需求高**：训练需大量GPU（24×A800 + 8×A100），阻碍小团队复现或扩展。
- **未报告统计显著性**：实验使用固定种子，未给出误差棒或置信区间，可靠性分析可进一步加强。
- **主观评估规模有限**：仅15名评估员，样本量可扩大。

（完）
