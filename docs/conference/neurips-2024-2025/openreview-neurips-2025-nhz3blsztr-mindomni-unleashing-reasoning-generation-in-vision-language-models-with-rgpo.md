---
title: "MindOmni: Unleashing Reasoning Generation in Vision Language Models with RGPO"
title_zh: MindOmni：通过RGPO在视觉语言模型中释放推理生成能力
authors: "Yicheng Xiao, Lin Song, Yukang Chen, Yingmin Luo, Yuxin Chen, Yukang Gan, Wei Huang, Xiu Li, XIAOJUAN QI, Ying Shan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=NHz3BlszTR"
tags: ["query:mm-cot"]
score: 9.0
evidence: 统一多模态模型，结合CoT与RGPO进行推理
tldr: 当前文本到图像系统难以处理多模态输入和复杂推理。MindOmni通过三阶段训练（统一视觉语言模型、CoT指令微调、推理生成策略优化RGPO）实现多模态推理生成。实验表明其在理解和推理任务上均优于现有模型，为多模态推理模型提供了新的训练范式。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 208, \"height\": 209, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 212, \"height\": 210, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 216, \"height\": 215, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1431, \"height\": 690, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1443, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 429, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 431, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 739, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 427, \"height\": 270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1440, \"height\": 843, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1440, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1433, \"height\": 1810, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 214, \"height\": 214, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 211, \"height\": 216, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 220, \"height\": 220, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 218, \"height\": 219, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 215, \"height\": 212, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 212, \"height\": 208, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 217, \"height\": 219, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nhz3blsztr/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 211, \"height\": 211, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhz3blsztr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1399, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhz3blsztr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1461, \"height\": 893, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhz3blsztr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 720, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhz3blsztr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 587, \"height\": 468, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhz3blsztr/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 577, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhz3blsztr/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 622, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhz3blsztr/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 434, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhz3blsztr/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 488, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nhz3blsztr/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 472, \"height\": 280, \"label\": \"Table\"}]"
motivation: 现有文本到图像系统缺乏多模态理解和复杂推理能力，需要统一的推理生成框架。
method: 设计包含解码器扩散模块的统一视觉语言模型，使用CoT指令数据和RGPO算法进行三阶段训练。
result: 在多项理解和推理任务上超越现有模型，展示了强大的推理生成能力。
conclusion: 验证了通过强化学习优化推理生成在多模态领域的效果，为后续研究奠定了基础。
---

## Abstract
Recent text-to-image systems face limitations in handling multimodal inputs and complex reasoning tasks.
We introduce MindOmni, a unified multimodal large language model that addresses these challenges by incorporating reasoning generation through reinforcement learning. MindOmni leverages a three-phase training strategy: i) design of a unified vision language model with a decoder-only diffusion module, ii) supervised fine-tuning with Chain-of-Thought (CoT) instruction data, and iii) our proposed Reasoning Generation Policy Optimization (RGPO) algorithm, utilizing multimodal feedback to effectively guide policy updates.
Experimental results demonstrate that MindOmni outperforms existing models, achieving impressive performance on both understanding and generation benchmarks, meanwhile showcasing advanced fine-grained reasoning generation capabilities,  especially with mathematical reasoning instruction. All codes will be made public.

---

## 论文详细总结（自动生成）

# 论文详细总结：MindOmni：通过RGPO在视觉语言模型中释放推理生成能力

## 1. 核心问题与整体含义（研究动机和背景）

**核心问题**：现有文本到图像（Text-to-Image）系统存在两大局限：
- 使用固定文本编码器，只能接受文本指令，无法有效融合图像、音频等多模态输入；
- 缺乏显式推理能力，难以处理需要世界知识、数学逻辑或时空感知的复杂生成任务（例如“生成一张动物图片，该动物有(3+6)条命”）。

**整体含义**：本文旨在构建一个统一的**多模态大语言模型（MLLM）**，能够同时进行视觉理解、文本到图像生成和推理引导的图像生成。通过引入强化学习（特别是组相对策略优化GRPO的改进版本RGPO），激发模型自动生成链式思维（Chain-of-Thought, CoT）并用于指导图像生成，从而弥合视觉-语言模型（VLM）与生成模型之间的鸿沟。

## 2. 方法论：核心思想、关键技术细节、算法流程

**核心思想**：三阶段训练策略，逐步实现从基础生成到推理引导的生成。

**阶段一：统一视觉语言模型搭建（预训练）**
- 使用**Qwen2.5-VL**作为骨干视觉语言模型（VLM），**OmniGen**的仅解码器扩散模块（diffusion decoder）作为图像生成器。
- 引入**轻量级连接器**（两个标准LLM解码器层）桥接VLM与扩散解码器。
- 训练目标：扩散损失 + KL蒸馏损失（保持与教师模型的一致性），仅训练连接器。
- 数据：LAION COCO、JourneyDB图像-文本对，以及X2I数据集（含计算机视觉任务、上下文学习等）。

**阶段二：监督微调（SFT）**
- 构造**粗到细的CoT指令数据**：粗粒度描述作为答案内容，细粒度描述作为推理内容。利用先进文本到图像模型（如Sana、FLUX）生成对应高质量图像。
- 训练连接器和扩散解码器，仅使用扩散损失。

**阶段三：推理生成策略优化（RGPO）**
- 基于DeepSeek-R1的GRPO算法改进，核心创新：
  - **多模态奖励信号**：不仅有文本格式奖励（判断是否包含 `<think>` 和 `<answer>` 标签），还引入**一致性奖励**（用CLIP图像和文本编码器计算生成图像与真实提示的余弦相似度）。
  - **双重KL散度正则化**：分别对文本生成和图像生成施加KL散度，防止偏离参考模型，稳定训练并缓解知识遗忘。
  - 策略优化目标（公式7）：  
    \( L_{\text{GRPO}} = - \mathbb{E} \left[ \frac{1}{G}\sum_{i=1}^G \min\left( \frac{\pi_\theta(o_i|q)}{\pi_{\theta_{\text{old}}}(o_i|q)} A_i, \text{clip}(\dots, 1-\epsilon, 1+\epsilon) A_i \right) - \beta_T D^T_{KL} - \beta_I D^I_{KL} \right] \)
  - 其中，优势 \(A_i\) 基于组内奖励标准化计算。

**推理流程**：
- 系统提示引导模型输出 ` <think>推理过程</think><answer>文本描述<IMG></answer> `。
- 遇到特殊token `<IMG>` 时，通过连接器将最后隐藏状态对齐到扩散解码器维度，并与噪声隐变量、时间步token拼接，经多轮去噪生成图像。

## 3. 实验设计：数据集、Benchmark、对比方法

**数据集**：
- 预训练：LAION COCO（600M合成字幕）、JourneyDB、X2I数据集。
- 第二阶段SFT：自构CoT指令数据（粗/细粒度描述，用Sana/FLUX生成图像）。
- 第三阶段RGPO：纯文本推理训练数据（由Qwen3生成）。

**基准（Benchmark）**：
- **理解**：MMMU（多学科多模态理解）、MMBench（多模态基准）、RealworldQA（现实世界问答）。
- **基本生成**：GenEval（对象层级对齐）、DPG-Bench（密集提示生成）。
- **推理生成**：WISE（世界知识语义评估，涵盖文化、时空、自然科学（生物、物理、化学））。

**对比方法**：
- 纯生成模型：SDv1-5、PixArt、SDXL、FLUX、Sana-1.5、OmniGen、SimpleAR等。
- 理解与生成统一模型：Chameleon、Show-o、Janus、Janus-Pro、TokenFlow-XL、MetaQuery-XL、BLIP-3o、BAGEL、GoT、MetaMorph等。
- 商业模型：GPT-4o、Gemini-2.5。

**主要结果**（表格中摘录）：
- 在**WISE**上：MindOmni* 整体得分 **0.71**，远超之前最优的BAGEL（0.70）和FLUX（0.50），在所有子类别（文化、时空、科学）均领先。
- 在**GenEval**上：MindOmni 整体得分 **0.83**（变体0.83），高于Janus-Pro的0.80，与OmniGen（0.70）等拉开差距。
- 在**理解任务**上：MindOmni 在MMMU上51.6%，比Janus-Pro（41.0%）高10.6%，与Qwen2.5-VL（51.1%）接近，说明RL阶段未损失理解能力。

## 4. 资源与算力

文中未明确给出GPU型号、数量和总训练时长。仅在附录A.1中提到训练细节：
- 第一阶段：batch size 1024，图像分辨率256×256，学习率1e-4，权重衰减0.05。
- 第二阶段：分辨率提升至512×512，学习率降至5e-5。
- 第三阶段：采用余弦学习率调度器，组数G=4，KL系数βI=0.06, βT=0.01（默认）。

未提及使用的GPU类型（如A100、H100），也未说明训练总步数或耗时。这是本文的一个信息缺口。

## 5. 实验数量与充分性

**实验数量**：非常充分，涵盖：
- 三大类基准（理解、生成、推理生成）共7+个数据集/指标。
- 消融实验：
  - 三阶段有效性（表5）
  - 不同连接器类型（表6）
  - RGPO中KL系数、组数、奖励策略（表7、8、9）
- 定性比较（图6、7）：与GPT-4o、Gemini-2.5、FLUX等对比。
- 额外图像编辑任务验证（附录A.2，GEdit上的SC、PQ等）。

**充分性与公平性**：
- 对比方法涵盖主流模型，包括商业闭源模型。
- 使用官方或标准评估协议（如WISE、GenEval）。
- 报告了变体（使用更高质量数据MindOmni*），体现稳健性。
- 实验设计较为客观，但缺少跨模型推理生成的精确度量（如人工评估），主要依赖自动指标。

**不足**：未进行大规模黑盒对抗测试或安全评估；未分析低质量输入或罕见场景下的泛化能力。

## 6. 主要结论与发现

1. **三阶段训练策略**有效：预训练提供基础生成能力，SFT引入CoT模板，RGPO进一步优化推理质量；跳过SFT直接RL会导致生成下降。
2. **RGPO算法**关键：一致性奖励驱动推理生成对齐，文本和图像KL正则化保持基本生成能力；组数选择G=4最优。
3. **统一模型优势**：MindOmni在视觉理解上接近专用VLM（Qwen2.5-VL），同时在推理生成上显著超越纯生成模型和早期统一模型。
4. **数学推理能力特别突出**：可处理“x²+2=11”类方程，甚至操作棋盘（经过微调）。
5. **CoT长度并非越长越好**：图5显示，生成长度增加不一定带来更高WISE得分，仍需平衡。

## 7. 优点（方法或实验设计亮点）

1. **创新性**：首次将GRPO扩展为多模态RGPO，并成功应用于统一MLLM的推理生成，赋予模型端到端的显式推理能力。
2. **系统设计合理**：三阶段渐进式训练，从对齐到指令遵循再到强化学习，逻辑清晰，消融实验验证每个阶段必要性。
3. **全面评估**：覆盖理解、生成、推理生成三大维度，尤其推理生成基准WISE包含多学科细分任务，评测全面。
4. **可复现性与开放共享**：承诺开源所有代码（GitHub链接），提供详细训练超参数，易于社区复现。
5. **处理多模态输入**：支持图像/文本混合输入（如根据用户提供的蝌蚪图像生成青蛙），扩展应用场景。
6. **编辑能力突出**：保留参考图像的低级细节（纹理、布局），支持实例分割、棋盘等任务。

## 8. 不足与局限

1. **资源消耗未详细披露**：缺少算力报告（GPU类型、训练天数），不利于资源受限团队复现。
2. **推理生成质量依赖自动指标**：WISE为语义对齐评估，未引入人工评分或用户研究，可能未完全体现生成质量。
3. **多模态CoT为纯文本**：附录A.4指出“Chain-of-Thought内容为纯文本”，多模态CoT（如图文混合推理）留待未来工作，限制了更丰富的推理表达。
4. **效率与延迟未讨论**：未提供推理速度（每秒生成帧数）或计算复杂度分析，也未提及训练时长。
5. **泛化边界未探索**：实验集中在英文数据集和常见场景，对低资源语言、跨文化多样性、罕见概念等未进行测试。
6. **安全与偏见问题未涉及**：模型可能生成不当内容或强化刻板印象，文中未讨论任何过滤或伦理措施。
7. **编辑任务仅少量定量实验**：附录A.2只给出一个编辑基准（GEdit）的简单分数，缺乏与其他编辑方法的详细对比。

---

（完）
