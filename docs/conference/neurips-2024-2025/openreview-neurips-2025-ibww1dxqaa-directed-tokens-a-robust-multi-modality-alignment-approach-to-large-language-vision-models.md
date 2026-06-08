---
title: "Directed-Tokens: A Robust Multi-Modality Alignment Approach to Large Language-Vision Models"
title_zh: Directed-Tokens：面向大型语言-视觉模型的鲁棒多模态对齐方法
authors: "Thanh-Dat Truong, Huu-Thien Tran, Tran Thai Son, Bhiksha Raj, Khoa Luu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=iBwW1DxQaa"
tags: ["query:multimodal"]
score: 6.0
evidence: 鲁棒对齐提升多模态推理能力
tldr: 大型多模态模型在鲁棒性和泛化性上存在对齐问题。本文提出Directed-Tokens机制，通过重构图像顺序和文本顺序两种新任务，在预训练和微调阶段增强视觉与文本的鲁棒对齐。该方法提升了模型的推理能力和跨模态理解，实验证明了其有效性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ibww1dxqaa/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 724, \"height\": 826, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ibww1dxqaa/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 722, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ibww1dxqaa/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1443, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ibww1dxqaa/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 710, \"height\": 684, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ibww1dxqaa/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 734, \"height\": 314, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ibww1dxqaa/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 735, \"height\": 380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ibww1dxqaa/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1415, \"height\": 964, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ibww1dxqaa/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 721, \"height\": 119, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ibww1dxqaa/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1437, \"height\": 566, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ibww1dxqaa/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1437, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ibww1dxqaa/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 725, \"height\": 213, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ibww1dxqaa/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 726, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ibww1dxqaa/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 724, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ibww1dxqaa/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1433, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ibww1dxqaa/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1430, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ibww1dxqaa/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 664, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ibww1dxqaa/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 734, \"height\": 250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ibww1dxqaa/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1441, \"height\": 263, \"label\": \"Table\"}]"
motivation: 多模态模型中视觉与文本特征对齐不鲁棒，导致泛化能力受限。
method: 提出两个排序重构任务，在预训练和微调中学习鲁棒的跨模态对齐。
result: 实验显示该方法提高了模型推理、视觉理解和跨模态对齐的性能。
conclusion: 证明了简单有效的排序任务能显著改善多模态模型的对齐质量。
---

## Abstract
Large multimodal models (LMMs) have gained impressive performance due to their outstanding capability in various understanding tasks. However, these models still suffer from some fundamental limitations related to robustness and generalization due to the alignment and correlation between visual and textual features. In this paper, we introduce a simple but efficient learning mechanism for improving the robust alignment between visual and textual modalities by solving shuffling problems. In particular, the proposed approach can improve reasoning capability, visual understanding, and cross-modality alignment by introducing two new tasks: reconstructing the image order and the text order into the LMM's pre-training and fine-tuning phases. In addition,  we propose a new directed-token approach to capture visual and textual knowledge, enabling the capability to reconstruct the correct order of visual inputs. Then, we introduce a new Image-to-Response Guided loss to further improve the visual understanding of the LMM in its responses. The proposed approach consistently achieves state-of-the-art (SoTA) performance compared with prior LMMs on academic task-oriented and instruction-following LMM benchmarks.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **关键问题**：当前大型多模态模型（LMMs）虽然性能卓越，但存在视觉与文本特征对齐不鲁棒、模型过度依赖语言偏好而忽视视觉信息的缺陷。论文通过实验证实，移除图像输入后模型性能下降有限（例如LLaVA-1.5在ScienceQA-IMG和MMMU上仅分别下降2.7%和2.9%），说明视觉-文本对齐并未充分学习。
- **研究动机**：针对上述“视觉信息被忽视”的根本问题，论文提出利用图像块乱序和文本描述乱序的重构任务，强制模型必须依赖视觉信息完成正确排序，从而提升跨模态对齐的鲁棒性。
- **整体含义**：揭示了简单排序任务对于改善多模态表示学习的重要性，为后续研究提供了一个低成本、高效的通用改进思路。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：在LMM的预训练和微调阶段引入两个序重构任务（Image Order Reconstruction & Text Order Reconstruction），迫使模型同时利用视觉和文本信息恢复正确顺序，以此增强跨模态对齐。
- **关键技术细节**：
  - **Directed Token（drt）**：在输入序列末尾插入一个可学习标记，该标记通过自注意力机制同时聚合视觉与文本特征，用于预测图像块的乱序索引k。相比直接用视觉token，drt能更充分地融合多模态信息。
  - **图像顺序重构**：将图像快按patch打乱（patch size 14×14，共576个patch，随机选取10,000种排列），要求模型根据随机放置的图像和原始文本描述预测正确的排列索引k。训练时使用交叉熵损失。
  - **文本顺序重构（仅预训练阶段）**：将文本描述中的词语随机打乱，要求模型结合原始图像恢复正确的语序。训练时采用标准自回归损失，并在答案末尾添加drt以保持格式一致。
  - **Image-to-Response Guided Loss（L_{I→R}）**：在每一层注意力层中，最小化视觉token到响应token的注意力分数与1之间的差距，即鼓励视觉特征更多地流向模型输出，从而提升视觉信息在生成响应中的贡献。
- **公式与算法流程**：
  - 预训练总损失：`L_pretrain = L_CE + L_Image-Order + L_Text-Order + L_{I→R}`（L_CE为传统自回归语言建模损失）。
  - 微调总损失：`L_finetune = L_CE + L_Image-Order + L_{I→R}`（仅保留图像顺序重构，避免打乱文本破坏对话上下文）。
  - 图像顺序重构任务中，drt的隐藏状态经过线性投影层得到预测的排列索引k̂ = ProjectLN(drt_h)。

### 3. 实验设计：数据集、benchmark、对比方法

- **数据集与benchmark**：
  - **学术任务导向**：VQAv2、GQA、VizWiz、ScienceQA-IMG、TextVQA。
  - **指令跟随LMM**：POPE（random/popular/adversarial）、SEED-Bench（图像+视频）、MME、LLaVA-Wild、MM-Vet、MMMU-Val。
- **对比方法**：BLIP-2、InstructBLIP、Shikra、IDEFICS、Qwen-VL、LLaVA-1.5等，涵盖不同参数规模和视觉编码器。
- **实验设置**：沿用LLaVA v1.5的训练数据（558K预训练+665K微调），图像分辨率336×336，使用CLIP-ViT-L-14视觉编码器，语言模型采用Vicuna-7B/13B、Qwen-7B、LLaMA3-8B。

### 4. 资源与算力

- 实验使用了**32块NVIDIA A100 GPU**，采用LLaVA v1.5相同的超参数配置（具体训练时长未在论文中明确给出，但提到使用了A100集群）。

### 5. 实验数量与充分性

- **实验数量**：论文进行了丰富的对比实验和消融分析：
  - 主实验结果（表2、表3）覆盖11个基准，与8种以上先前方法对比。
  - 消融实验包括：
    1. 不同语言模型（Vicuna-7B/13B、Qwen-7B、LLaMA3-8B）的影响。
    2. 对图像重构任务使用“视觉token vs directed token”的比较。
    3. 预训练阶段“仅图像乱序、仅文本乱序、两者结合”的效果。
    4. 微调阶段是否加入图像乱序重构的影响。
    5. Image-to-Response Guided Loss有无的对比。
    6. 不同预训练/微调数据规模的对比（LLaVA v1 vs v1.5规模）。
    7. 扩展到更大的LLaVA-OneVision数据集上的验证。
    8. 对drt放置位置（开头 vs 结尾）、排列数量（5k/10k/15k）的进一步分析。
- **充分性与公平性**：
  - 实验设计较为全面，结果一致支持方法有效性。
  - 所有对比均采用标准化benchmark和官方评估协议，对比基线均为已发表的最新结果。
  - **潜在偏差**：所有实验均基于LLaVA v1.5框架，未在不同架构（如InstructBLIP、Qwen-VL）上验证方法的通用性，但论文指出方法原理上可迁移。

### 6. 论文的主要结论与发现

- 提出的Direct-LLaVA在所有12个基准上均超越LLaVA-1.5等基线，在ScienceQA-IMG、TextVQA等任务上提升幅度显著（如ScienceQA-IMG从71.6%提至77.3%）。
- 图像顺序重构和文本顺序重构的联合训练带来最大增益；单独使用图像重构效果优于单独使用文本重构。
- Directed Token相比视觉token能更有效地捕获跨模态线索，用于排列预测。
- Image-to-Response Guided Loss可进一步对齐视觉与文本特征，提升模型在注意力层面的视觉依赖性。
- 方法在更大模型（Vicuna-13B）和更大数据规模（LLaVA-OneVision数据）下依然有效，说明具有良好的可扩展性。

### 7. 优点：方法或实验设计上的亮点

- **简洁高效**：仅通过添加简单的排序任务和一个可学习token，无需额外大规模数据或复杂网络结构，即可显著提升对齐质量。
- **创新性**：首次将“乱序重构”这一自监督学习范式系统性地引入LMM微调阶段，并专门设计了directed token和I→R loss来支持该任务。
- **实验充分**：在多个维度进行了严格的消融实验，验证了每个组件的贡献，且在不同模型大小和数据规模上均有一致性表现。
- **关注实际问题**：深入分析了现有LMM对视觉信息的忽视现象，并提供了可量化的证据（表1），使研究动机非常扎实。

### 8. 不足与局限

- **目标平衡未探索**：三个损失函数（L_CE、L_Image-Order、L_Text-Order、L_{I→R}）的权重固定为1，未进行权重调优，可能不是最优平衡。
- **架构通用性待验证**：所有实验基于LLaVA系列（CLIP视觉编码器+自回归语言模型），在Q-Former或交叉注意力等不同架构上的表现尚未确认。
- **计算开销**：虽然方法本身轻量，但预训练阶段需要额外生成打乱图像和文本，且需前向传递计算随机排列，可能增加少量训练时间，但论文未量化额外开销。
- **文本顺序重构仅在预训练中使用**：微调阶段由于担心破坏对话上下文而舍弃了文本乱序任务，或许存在更好的策略（如仅在部分样本上使用）。
- **排列选择依赖随机采样**：10,000种排列虽能保证一定多样性，但未探讨更优的排列选择策略（如基于难度的自适应选取）。

（完）
