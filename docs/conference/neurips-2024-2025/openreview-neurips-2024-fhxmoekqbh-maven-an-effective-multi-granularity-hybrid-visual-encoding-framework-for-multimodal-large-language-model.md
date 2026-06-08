---
title: "MaVEn: An Effective Multi-granularity Hybrid Visual Encoding Framework for Multimodal Large Language Model"
title_zh: MaVEn：面向多模态大语言模型的高效多粒度混合视觉编码框架
authors: "Chaoya Jiang, Jia Hongrui, Haiyang Xu, Wei Ye, Mengfan Dong, Ming Yan, Ji Zhang, Fei Huang, Shikun Zhang"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=fHxmoekQBh"
tags: ["query:mm-cot"]
score: 7.0
evidence: 多粒度视觉编码增强多图像推理
tldr: 当前多模态大语言模型（MLLM）主要处理单图像，跨图像推理能力不足。MaVEn提出多粒度混合视觉编码框架，融合离散视觉符号序列（粗粒度语义）与连续表示序列（细粒度特征），弥补视觉与文本的语义鸿沟。实验证明该方法在多图像推理任务上显著提升MLLM的性能。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-fhxmoekqbh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 653, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fhxmoekqbh/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1440, \"height\": 640, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fhxmoekqbh/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1432, \"height\": 640, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fhxmoekqbh/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1432, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fhxmoekqbh/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1453, \"height\": 687, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fhxmoekqbh/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1437, \"height\": 615, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-fhxmoekqbh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 439, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fhxmoekqbh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1383, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fhxmoekqbh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1443, \"height\": 541, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fhxmoekqbh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1312, \"height\": 193, \"label\": \"Table\"}]"
motivation: 现有MLLM难以整合多图像信息，对跨图像推理支持有限。
method: 设计多粒度编码，同时使用离散符号和连续表示编码图像特征。
result: 在多图像推理基准上取得性能提升。
conclusion: 提供了一种有效的多图像视觉编码方案，增强了MLLM的多图理解能力。
---

## Abstract
This paper presents MaVEn, an innovative Multi-granularity Visual Encoding framework designed to enhance the capabilities of Multimodal Large Language Models (MLLMs) in multi-image reasoning. Current MLLMs primarily focus on single-image visual understanding, limiting their ability to interpret and integrate information across multiple images. MaVEn addresses this limitation by combining discrete visual symbol sequences, which abstract coarse-grained semantic concepts, with traditional continuous representation sequences that model fine-grained features. This dual approach bridges the semantic gap between visual and textual data, thereby improving the model's ability to process and interpret information from multiple images effectively. Additionally, we design a dynamic reduction mechanism by for long-sequence continuous features to enhance multi-image processing efficiency. Experimental results demonstrate that MaVEn significantly enhances MLLMs' understanding in complex multi-image scenarios, while also improving performance in single-image contexts.

---

## 论文详细总结（自动生成）

# MaVEn：面向多模态大语言模型的高效多粒度混合视觉编码框架——中文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：当前多模态大语言模型（MLLM）主要针对单图像场景设计，在跨多图像的理解与推理任务中表现不佳，主要原因包括：
  - 现有视觉编码方法（连续序列或离散符号）单一，难以同时兼顾粗粒度语义抽象与细粒度细节；
  - 连续视觉特征序列过长，在多图像输入时导致计算开销大且上下文长度受限；
  - 视觉与文本之间的语义鸿沟依然明显，模型对多图像信息的整合能力有限。
- **整体含义**：旨在提出一种多粒度混合视觉编码框架MaVEn，通过融合离散符号序列（捕获高层次语义）与连续表示序列（保留细粒度特征），并设计动态压缩机制，来显著提升MLLM在多图像推理场景下的性能，同时保持甚至改善单图像任务的表现。

## 2. 论文提出的方法论
### 核心思想
- 同时利用两种互补的视觉编码：
  - **离散视觉编码**：使用SEED离散化图像为32个离散符号序列，抽象出粗粒度语义概念，与文本离散表示在语义空间上更对齐。
  - **连续视觉编码**：使用Vision Transformer（ViT）提取图像patch的连续向量序列，保留细粒度细节。
- 两种编码通过**统一多模态词汇表**合并，离散视觉词汇被加入LLM的嵌入层，实现跨模态统一表示。
- 设计**动态连续视觉令牌缩减机制**（Patch Selector），根据离散视觉令牌的全局语义（由LLM输出的EOS令牌隐状态表征）预测每个patch的相关性得分，保留最相关的top-m个patch（保持率α=0.25），丢弃冗余令牌，从而压缩连续序列长度（从576降至144）。
- 训练分四个阶段：
  1. 训练Patch Selector（基于Grounding SAM生成的伪标签）；
  2. 训练LLM的嵌入层以适应扩展词汇表（仅用离散编码）；
  3. 训练视觉投影器（仅用连续编码）；
  4. 全参数微调（冻结视觉编码器和Patch Selector）进行指令微调。

### 关键技术细节
- **输入格式**：每张图像最终表示为`[连续令牌序列 (144个) + 离散令牌序列 (32个)]`，总长度176。
- **Patch Selector**：MLP（3层线性+Sigmoid），输入为每个patch向量与离散EOS隐状态的拼接，输出相关性得分。
- **伪标签生成**：利用Grounding SAM对图像进行文本引导语义分割，计算每个patch与分割掩码的重叠，生成0/1标签。
- **优化器**：AdamW；指令微调阶段学习率2e-5，batch size 256。

## 3. 实验设计
### 数据集与场景
- **多图像场景**：
  - **DemonBench**（7个子任务）：多模态对话、视觉故事讲述、视觉关系推理、多模态完形填空、知识型VQA、文本丰富图像QA、多图像推理。
  - **SEED-Bench**：视频理解任务（动作预测、动作识别、过程理解）。
- **单图像场景**：
  - **VQA**：VQAv2、GQA、VizWizQA、TextVQA、SciQA。
  - **多模态benchmark**：MME、MMBench、MM-Vet。
- **训练数据**：
  - 阶段1：COCO、Visual Genome、RefCOCO（生成100万伪标签）。
  - 阶段2：MMC4-core + LLaVA 558K单图像预训练数据。
  - 阶段3：LLaVA 558K。
  - 阶段4：LLaVA 665K指令微调数据。

### 对比方法
- 多图像方法：BLIP-2、mPLUG-Owl、InstructBLIP、LLaMA-Adapter-v2、LLaVA、MiniGPT-4、LLaVA-1.5、Otter、OpenFlamingo、VPG-C。
- 单图像方法：BLIP-2、InstructBLIP、Unified-IO XL、PaLM-E-12B、Shikra、Qwen-VL-Chat、LLaVA、MiniGPT-4、LLaVA-1.5等。

## 4. 资源与算力
- **明确说明**：所有实验在8块NVIDIA A100 GPU（每块80GB显存）上完成。训练时间未具体给出，但总模型参数量为7.2B（ViT-L + SEED + Vicuna-7B）。

## 5. 实验数量与充分性
- **实验覆盖**：
  - 主实验：在DemonBench（7项任务）和SEED-Bench（视频理解）上做零样本评测，与多家方法对比。
  - 单图像评测：5个VQA数据集 + 3个多模态benchmark。
  - 消融实验：
    - 多粒度编码有效性（仅离散、仅连续、混合）。
    - 连续令牌缩减机制（保持率从0.1到1.0的对比）。
    - 定性分析：注意力可视化、离散令牌语义可视化。
- **充分性与公平性**：
  - 对比方法均为公开主流模型，设置公平（相同LLM骨干Vicuna-7B）。
  - 消融实验覆盖了关键组件，验证了各模块贡献。
  - 实验涵盖了多图像和单图像两类任务，评价指标全面。

## 6. 论文的主要结论与发现
- **多图像理解**：MaVEn在DemonBench的5/7任务上取得最高分（如视觉关系推理、多模态完形填空、文本丰富图像QA、知识型VQA、多图像推理），在SEED-Bench视频理解上显著优于LLaVA-1.5等基线（42.11 vs 37.3）。
- **单图像理解**：MaVEn在VQAv2、GQA、VizWizQA、TextVQA、SciQA上全面超越LLaVA-1.5，并在MME、MMBench、MM-Vet上保持领先或相当。
- **消融证明**：
  - 混合编码优于仅离散或仅连续编码，尤其在多图像任务上提升明显。
  - 保持率0.25是效率与性能的最佳平衡点（序列长度从576降至176，性能损失极小）。
- **定性分析**：
  - 离散令牌（如索引4568）对应高层的语义概念（雪人），且位置一致。
  - Patch Selector倾向于选择与离散语义相关的patch，补充细粒度信息。
  - 注意力可视化表明，混合编码帮助模型在推理时关注视觉令牌（尤其是离散令牌），而仅连续编码时模型主要关注文本令牌。

## 7. 优点
- **创新性**：首次将离散与连续视觉编码混合用于多图像推理，利用离散符号弥补语义鸿沟，连续特征保留细节。
- **效率设计**：动态令牌缩减机制显著降低序列长度，使多图像输入可行且高效。
- **训练策略**：四阶段训练解耦了不同组件的学习目标，避免相互干扰，且充分利用了现有监督信号（如Grounding SAM生成伪标签）。
- **实验全面**：覆盖多图像和单图像多种任务，并提供了详细的消融与定性分析，证实了各模块的有效性。
- **性能优秀**：在多图像基准上大幅超越基线，且不牺牲单图像性能，实现了双赢。

## 8. 不足与局限
- **实验偏差风险**：
  - 伪标签依赖Grounding SAM，其本身的错误可能带入噪声；文中未分析伪标签质量对结果的影响。
  - 训练数据仅使用了公开数据集（COCO、VG等），未在更复杂、更真实的多图像场景（如医学影像、新闻多图）上验证。
- **应用限制**：
  - 离散编码器SEED需要额外预训练，且词汇表大小固定，可能限制对未见概念的泛化。
  - 保持率α=0.25是手动设定的，不同任务或图像复杂度可能需要自适应调整，文中未提供自适应策略。
  - 模型参数量7.2B，推理时仍需要同时运行ViT和SEED两个编码器，计算成本高于单编码器方案。
- **理论分析**：缺乏对离散与连续表示互补性的理论解释或形式化证明。
- **复现性**：未提供开源代码和数据，关键细节（如训练超参数的具体值、伪标签生成代码）需依赖后续开放。

（完）
