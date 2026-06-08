---
title: "I Think, Therefore I Diffuse: Enabling Multimodal In-Context Reasoning in Diffusion Models"
title_zh: 我思故我绘：赋予扩散模型多模态上下文推理能力
authors: "Zhenxing Mi, Kuan-Chieh Wang, Guocheng Qian, Hanrong Ye, Runtao Liu, Sergey Tulyakov, Kfir Aberman, Dan Xu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=2v91xhNdsz"
tags: ["query:mm-cot"]
score: 8.0
evidence: 扩散模型的多模态上下文推理
tldr: 当前多模态扩散微调方法多关注像素级重建而非上下文推理，且受限于推理数据集。本文提出ThinkDiff，通过视觉-语言训练作为代理任务，将视觉语言模型与编码器-解码器LLM的decoder对齐，赋予扩散模型多模态上下文理解和推理能力，无需专门的推理数据集。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1743, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 854, \"height\": 801, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 852, \"height\": 296, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1761, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1767, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1759, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 691, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 854, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1436, \"height\": 2290, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1744, \"height\": 1825, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1757, \"height\": 2146, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1410, \"height\": 2165, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1617, \"height\": 1862, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2v91xhndsz/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1713, \"height\": 2156, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-2v91xhndsz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1773, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2v91xhndsz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1771, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2v91xhndsz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1767, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2v91xhndsz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 695, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2v91xhndsz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 864, \"height\": 155, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2v91xhndsz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1775, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2v91xhndsz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 863, \"height\": 260, \"label\": \"Table\"}]"
motivation: 现有多模态扩散微调缺乏上下文推理能力且依赖推理数据集。
method: ThinkDiff通过代理任务将视觉语言模型与LLM解码器对齐。
result: 在多个多模态推理任务上展示了有效性和泛化能力。
conclusion: 为扩散模型集成多模态推理提供了新范式。
---

## Abstract
This paper presents ThinkDiff, a novel alignment paradigm that empowers text-to-image diffusion models with multimodal in-context understanding and reasoning capabilities by integrating the strengths of vision-language models (VLMs). Existing multimodal diffusion finetuning methods largely focus on pixel-level reconstruction rather than in-context reasoning, and are constrained by the complexity and limited availability of reasoning-based datasets. ThinkDiff addresses these challenges by leveraging vision-language training as a proxy task, aligning VLMs with the decoder of an encoder-decoder large language model (LLM) instead of a diffusion decoder. This proxy task builds on the observation that the **LLM decoder** shares the same input feature space with **diffusion decoders** that use the corresponding **LLM encoder** for prompt embedding. As a result, aligning VLMs with diffusion decoders can be simplified through alignment with the LLM decoder. Without complex training and datasets, ThinkDiff effectively unleashes understanding, reasoning, and composing capabilities in diffusion models. Experiments demonstrate that ThinkDiff significantly improves accuracy from 19.2% to 46.3% on the challenging CoBSAT benchmark for multimodal in-context reasoning generation, with only 5 hours of training on 4 A100 GPUs. Additionally, ThinkDiff demonstrates exceptional performance in composing multiple images and texts into logically coherent images. Project page: https://mizhenxing.github.io/ThinkDiff.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：现有文本到图像扩散模型主要遵循显式提示生成高质量图像，但**缺乏多模态上下文推理能力**，例如无法从“飞行的猴子”和“飞行的猫”推理出下一个应该是“飞行的斑马”。这种能力有助于理解复杂指令、解决视觉类比问题、组合多模态输入生成逻辑一致图像。
- **核心问题**：当前多模态扩散微调方法（如IP-Adapter、ControlNet）**聚焦于像素级重建**，而非上下文推理，且需要复杂的推理数据集，难以获得和扩展。同时，直接对扩散模型进行推理训练成本高、泛化差。
- **整体含义**：论文提出**ThinkDiff**，通过**代理任务**将视觉语言模型（VLM）的强大推理能力迁移至扩散模型，使扩散模型能够“先思考后生成”，显著提升多模态上下文推理和组合生成能力，且训练高效、无需专用推理数据集。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用**编码器-解码器LLM**（如T5）的**共享特征空间**——扩散模型使用LLM编码器作为提示编码器，LLM解码器与扩散解码器输入特征空间一致。因此，**对齐VLM与LLM解码器**即可间接对齐VLM与扩散解码器。通过**视觉-语言训练**（使用图像-描述对）作为代理任务来训练对齐网络。

- **关键组成**：
  - **源VLM**：提供多模态特征。两种变体：
    - **ThinkDiff-LVLM**：使用大视觉语言模型（LVLM，如Qwen2-VL），抽取**生成令牌的深度特征**，捕获推理过程。
    - **ThinkDiff-CLIP**：使用CLIP视觉编码器，抽取图像令牌。
  - **对齐网络（Aligner Network）**：轻量模块，由两层线性层 + GELU + RMSNorm组成，将VLM特征映射到LLM解码器可解释的特征空间。**RMSNorm的初始化**使用LLM编码器最后一层的参数，确保训练稳定。
  - **解码器**：训练时使用**LLM解码器**，推理时替换为**扩散解码器**（如FLUX.1-dev）。LLM解码器将对齐后的特征自回归解码为文本，通过**交叉熵损失**监督。

- **关键技术细节（解决收敛与捷径问题）**：
  - **随机掩码训练**（针对ThinkDiff-LVLM）：将LVLM生成的令牌和特征随机分为两部分，仅传递第一部分，监督第二部分，打破令牌一一对应的“捷径映射”，强制学习上下文推理。
  - **使用生成令牌而非输入令牌**：因为推理嵌入在生成过程中，生成令牌特征更能捕获逻辑关系。

- **训练流程**：图像和文本 → VLM生成令牌特征 → 对齐网络 → LLM解码器 → 预测文本，与真值文本计算交叉熵损失。仅训练对齐网络，其他部分冻结。

### 3. 实验设计：数据集、Benchmark、对比方法

- **Benchmark**：**CoBSAT**，包含10个多模态上下文推理生成任务（如颜色、风格、动作、纹理等），分为2-shot和4-shot设置。
- **训练数据集**：CC3M、CC12M、SBU等公开图像-描述对（约1.7M图像），无需专门推理数据集。
- **对比方法**：
  - **ThinkDiff-LVLM**：对比SEED-LLaMA、Emu、GILL（三者均可基于图像和文本输入生成图像）。
  - **ThinkDiff-CLIP**：对比FLUX1.1-pro-Ultra（推测为重建微调方法）。
  - 额外对比：Janus Pro、Flux Redux、不同VLM（InternVL2.5-8B、Qwen2-VL-72B）。
- **其他实验设置**：
  - **图像质量评估**：在COCO 1K图像上评估FID、CLIP-I、CLIP-T；在GenEval和DPG-Bench上评估文本条件生成质量。
  - **多图像+文本组合**：展示对2张输入图像、图像+文本、视频生成（替换CogVideoX扩散解码器）的定性结果。
  - **消融实验**：RMSNorm初始化、随机掩码、是否使用生成令牌、数据规模、对比学习替代等。

### 4. 资源与算力

- **ThinkDiff-LVLM**：在 **4张A100 GPU**上训练 **5小时**，总批量96。
- **ThinkDiff-CLIP**：在 **4张A100 GPU**上训练 **1天**，总批量168。
- **对比方法资源**：SEED-LLaMA需64张A100训练216小时；Emu需128张A100训练48小时；GILL需2张A6000训练48小时。ThinkDiff显著降低了算力需求。

### 5. 实验数量与充分性

- **实验数量**：较为充分，包括：
  - 主要推理任务：CoBSAT的2-shot/4-shot共10类任务。
  - 图像质量：COCO、GenEval、DPG-Bench。
  - 定性示例：多图组合、图像+文本、视频生成。
  - 消融实验：RMSNorm、随机掩码、输入vs生成令牌、数据规模、不同VLM、对比学习。
  - 对比不同LVLM和更大模型（72B）。
- **公平性与客观性**：使用公开基准和标准指标（准确率、FID、CLIP分数），对比方法均为同期SOTA。消融实验控制变量，结果客观。但部分定性比较仅展示少数示例。

### 6. 论文的主要结论与发现

- **推理能力大幅提升**：在CoBSAT上，ThinkDiff-LVLM将平均准确率从19.2%（SEED-LLaMA）提升至46.3%（2-shot）/ 46.3%（4-shot平均达到0.463），9/10任务达到SOTA。
- **训练高效**：仅需5小时训练（4 A100），远低于对比方法（216小时）。
- **多模态组合能力**：能自然地将多个图像和文本融合为逻辑一致的新图像，优于重建型方法（如FLUX Ultra）。
- **通用性**：可扩展至视频生成（替换CogVideoX解码器），不限于特定扩散模型。

### 7. 优点：方法或实验设计上的亮点

- **创新代理任务**：巧妙利用LLM编码器-解码器的共享特征空间，将对齐扩散解码器转化为对齐LLM解码器，大大简化训练、消除对推理数据集的依赖。
- **轻量且迁移性强**：仅训练一个轻量对齐网络，冻结VLM和扩散模型，可实现快速迁移。
- **解决训练难题**：
  - RMSNorm初始化保证收敛。
  - 随机掩码训练解决捷径映射。
  - 使用生成令牌而非输入令牌，更准确传递推理信息。
- **实验设计全面**：既在推理基准上定量评估，又展示了多种组合生成示例，消融实验涵盖多个方面，逻辑清晰。

### 8. 不足与局限

- **推理准确性仍有提升空间**：尽管大幅超越基线，但在某些复杂案例中仍会出错（论文自身提及）。
- **主要聚焦逻辑推理，而非保真度**：论文指出对图像保真度的关注相对较少，限制了在图像编辑等任务的应用。
- **评估任务有限**：仅使用CoBSAT一个基准，虽然任务多样，但仍需更多真实场景下的推理任务来验证泛化性。
- **依赖特定模型**：当前基于FLUX和T5，若更换其他架构的扩散模型，需重新验证共享特征空间假设。
- **定性结果存在选择偏差**：论文展示的成功案例较多，未见失败案例的详细分析。
- **潜在应用限制**：存在生成误导内容的风险，但论文提及需负责任部署。

（完）
