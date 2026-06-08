---
title: "MMaDA: Multimodal Large Diffusion Language Models"
title_zh: MMaDA：多模态大型扩散语言模型
authors: "Ling Yang, Ye Tian, Bowen Li, Xinchen Zhang, Ke Shen, Yunhai Tong, Mengdi Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=wczmXLuLGd"
tags: ["query:mm-cot"]
score: 10.0
evidence: 跨模态混合长链思维微调
tldr: MMaDA提出一类多模态扩散基础模型，采用统一扩散架构和模态无关设计。核心创新是混合长链思维微调策略，统一文本和视觉领域的推理格式。该模型在文本推理、多模态理解和文生图任务上均表现优异。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 1148, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 1111, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 592, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1438, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 789, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 479, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 850, \"height\": 636, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 847, \"height\": 636, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 303, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 306, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 346, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 305, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 306, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 345, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 306, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 305, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 305, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 303, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 345, \"height\": 347, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 306, \"height\": 304, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 303, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 347, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 305, \"height\": 304, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 306, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 348, \"height\": 322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 350, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 545, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 544, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1308, \"height\": 1289, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 478, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 478, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 481, \"height\": 478, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wczmxlulgd/fig-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 486, \"height\": 497, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-wczmxlulgd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 695, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wczmxlulgd/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 609, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wczmxlulgd/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1450, \"height\": 594, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wczmxlulgd/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1296, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wczmxlulgd/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 663, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wczmxlulgd/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1450, \"height\": 804, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wczmxlulgd/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1440, \"height\": 191, \"label\": \"Table\"}]"
motivation: 现有模型在多模态任务中需要特定组件，缺乏统一推理框架。
method: 采用统一扩散架构和模态无关设计，并实施混合长链CoT微调。
result: 在文本推理、多模态理解和文生图多个任务上达到领先性能。
conclusion: 统一扩散架构和长链CoT微调能有效提升多模态模型的推理能力。
---

## Abstract
We introduce MMaDA, a novel class of multimodal diffusion foundation models designed to achieve superior performance across diverse domains such as textual reasoning, multimodal understanding, and text-to-image generation. The approach is distinguished by three key innovations: (i) MMaDA adopts a unified diffusion architecture with a shared probabilistic formulation and a modality-agnostic design, eliminating the need for modality-specific components. This architecture ensures seamless integration and processing across different data types. (ii) We implement a mixed long chain-of-thought (CoT) fine-tuning strategy that curates a unified CoT format across modalities. By aligning reasoning processes between textual and visual domains, this strategy facilitates cold-start training for the final reinforcement learning (RL) stage, thereby enhancing the model's ability to handle complex tasks from the outset. (iii) We propose UniGRPO, a unified policy-gradient-based RL algorithm specifically tailored for diffusion foundation models. Utilizing diversified reward modeling, UniGRPO unifies post-training across both reasoning and generation tasks, ensuring consistent performance improvements. Experimental results demonstrate that MMaDA-8B exhibits strong generalization capabilities as a unified multimodal foundation model. It surpasses powerful models like LLaMA-3-7B and Qwen2-7B in textual reasoning, outperforms Show-o and SEED-X in multimodal understanding, and excels over SDXL and Janus in text-to-image generation. These achievements highlight MMaDA's effectiveness in bridging the gap between pretraining and post-training within unified diffusion architectures, providing a comprehensive framework for future research and development. We open-source our code and trained models at: https://github.com/Gen-Verse/MMaDA

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）在文本推理和生成上取得突破，但其在多模态领域的扩展（MLLM/VLM）主要依赖**自回归（AR）架构**或**AR+扩散混合架构**，这些方法通常需要为不同模态设计专门的组件或损失函数（如文本使用AR、图像使用连续扩散）。此外，现有工作大多聚焦于**预训练策略**，对**后训练方法（post-training）** 在非自回归扩散模型中的探索严重不足，尤其缺乏针对统一多模态扩散模型的强化学习（RL）算法。
- **整体含义**：本文提出 **MMaDA**（Multimodal Large Diffusion Language Models），首次系统性地设计了一类**统一扩散基础模型**，通过模态无关的架构设计、混合长链思维（Long-CoT）微调和统一RL算法，弥合了预训练与后训练之间的鸿沟，在文本推理、多模态理解和文生图三类任务上同时达到领先性能，证明了扩散模型作为下一代多模态通用范式的潜力。

## 2. 方法论：核心思想、关键技术细节与算法流程

### 2.1 统一扩散架构与预训练目标
- **数据分词**：文本采用 LLaDA 的分词器，图像采用基于 MAGVIT-v2 的离散量化器（下采样因子16，码本大小8192），将图像转换为离散令牌序列。
- **统一概率建模**：所有模态均作为离散令牌，使用**离散扩散（掩码令牌预测）** 统一建模，避免混合损失函数。预训练损失仅计算被掩码的令牌：
  \[
  L_{\text{unify}}(\theta) = -\mathbb{E}_{t, x_0, x_t}\left[\frac{1}{t}\sum_{i=1}^L \mathbb{I}[x_i^t=\text{[MASK]}] \log p_\theta(x_i^0|x_t)\right]
  \]
  其中 \(t\) 从 [0,1] 均匀采样，\(x_t\) 由正向扩散得到。

### 2.2 混合长链思维（Mixed Long-CoT）微调
- **统一CoT格式**：使用 `<special_token> <reasoning_process> <special_token> <result>` 的格式，统一不同任务（文本、图像）的推理输出。
- **数据构建**：利用 DeepSeek-R1、GPT-4.1 等模型生成长链推理轨迹，经验证过滤低质量样本，覆盖数学推理、几何问题、世界知识驱动的文生图等任务。
- **训练方式**：保留原始提示 \(p_0\)，仅对结果部分 \(r_t\) 随机掩码，联合计算损失：
  \[
  L_{\text{Mixed-SFT}} = -\mathbb{E}_{t, p_0, r_0, r_t}\left[\frac{1}{t}\sum_{i=1}^{L'}\mathbb{I}[r_i^t=\text{[MASK]}] \log p_\theta(r_i^0|p_0, r_t)\right]
  \]
  使模型学会在上下文中恢复被掩码的推理和结果，形成冷启动初始化。

### 2.3 统一策略梯度RL算法（UniGRPO）
- **挑战**：自回归GRPO的令牌级对数似然无法直接应用于扩散模型，因为扩散依赖局部掩码，且无链式法则。
- **解决方案**：
  1. **结构化噪声**：为每个回答随机采样掩码比例 \(p_i\)，构造扰动版本 \(\tilde{o}_{i,p}\)。
  2. **对数似然近似**：定义期望的每令牌对数似然为扰动分布下的条件概率，序列级似然通过掩码令牌的平均值近似。
  3. **策略梯度目标**：
     \[
     J_{\text{UniGRPO}}(\theta) = \mathbb{E}_{q,\{o_i\},\{p_i\}}\left[\frac{1}{G}\sum_{i=1}^G\frac{1}{|o_i|}\sum_{t=1}^{|o_i|}\min(r'_{i,t}(\theta)\hat{A}_{i,t},\text{clip}(r'_{i,t}(\theta),1-\epsilon,1+\epsilon)\hat{A}_{i,t}) - \beta D_{\text{KL}}(\pi'_\theta\|\pi'_{\text{ref}})\right]
     \]
  4. **多样化奖励**：根据任务定制奖励（正确性奖励、格式奖励、CLIP分数、ImageReward等），统一在公式 \(R_{\text{Uni}}(\cdot)\) 下。

## 3. 实验设计

### 3.1 数据集与场景
- **文本数据**：RefinedWeb（基础语言建模）。
- **多模态数据**：ImageNet-1k、CC12M、SA1B、LAION-aesthetics-12M、JourneyDB。
- **指令数据**：Alpaca（文本）、LLaVA-1.5（视觉）。
- **推理数据**：LIMO、s1k、OpenThoughts、AceMath-Instruct（文本推理）；LMM-R1 生成 GeoQA、CLEVR 样本（多模态推理）；GPT-4.1 合成世界知识文生图样本。
- **RL数据**：GSM8K、GeoQA、CLEVR 等原始数据集。

### 3.2 Benchmark
- **多模态理解**：POPE、MME、Flickr30k、VQAv2、GQA、MMMU、MMB、SEED。
- **文生图**：CLIP Score、ImageReward、GenEval（对象计数/属性/位置）、WISE Natural（世界知识）。
- **文本生成**：MMLU、ARC-C、TruthfulQA、GSM8K、MATH、GPQA。

### 3.3 对比方法
- **理解专用模型**：LLaVA-v1.5、InstructBLIP、Qwen-VL-Chat、mPLUG-Owl2、LLaVA-Phi。
- **统一理解&生成模型**：DreamLLM、SEED-X、Chameleon、LWM、Emu、Show-o、Janus/Janus Pro、Gemini-Nano-1、VAR-GPT。
- **生成专用模型**：Stable Diffusion 1.5/2.1/XL、DALL-E 2、LlamaGen。
- **文本模型**：LLaMA2-7B、LLaMA3-8B、Qwen2-7B、LLaDA-8B、Dream-7B。

### 3.4 消融实验
- **表6**：在GSM8K、MATH500、GeoQA、CLEVR、CLIP Score、ImageReward上，逐步对比Stage1、Stage2（+Mixed Long-CoT）、Stage3（+UniGRPO）的性能提升。
- **图6**：对比 UniGRPO 与 diff-GRPO 在 GSM8K 上的奖励曲线，显示 UniGRPO 更稳定、更高。
- **图7**：均匀随机掩码 vs 完全随机掩码，均匀策略收敛更快、更稳定。

## 4. 资源与算力

- **GPU**：64块 NVIDIA A100 (80GB)。
- **训练步数**：
  - Stage1：200K步（基础语言+类条件图像）+ 400K步（多样化图文对），共600K步。
  - Stage2：50,000步（混合长CoT微调）。
  - Stage3：50,000步（UniGRPO RL训练）。
- **全局batch size**：1280。
- **优化器**：AdamW，初始学习率5e-5，余弦退火调度。

## 5. 实验数量与充分性

- **多模态理解**：8个基准数据集（Table 2），与11+个模型比较，数据覆盖广泛。
- **文生图**：4个评价指标（CLIP Score, ImageReward, GenEval, WISE），与12+个模型比较，含生成专用和统一模型。
- **文本生成**：6个基准（Table 4），与6个文本模型比较，涵盖通用知识和数学推理。
- **消融**：含3组主要消融（Stage-by-stage、RL掩码策略、随机策略），均给出量化结果。
- **协同分析**：图3展示训练过程中三个任务性能同步提升，定性例证在图4。
- **效率分析**：Table 5测试不同去噪步数下的性能。
- **扩展任务**：inpainting定性示例。
- 实验整体充分，基准和对比方法选择合理，结果呈现清晰。但某些数据集（如WISE）仅对比有限模型，另外部分对比模型（如DreamLLM）在部分表上缺失数据，可能影响公平性；不过作者已尽量列出公开数据。

## 6. 主要结论与发现

- MMaDA-8B在**多模态理解**上与专用理解模型相当甚至更优（POPA 86.1，VQAv2 76.7），显著超越统一模型（Show-o、SEED-X等）。
- 在**文生图**上，CLIP Score 32.46、ImageReward 1.15超越所有基线（含SDXL、Janus），GenEval总体0.63仅次于Janus的0.61（论文中写0.63 vs 0.61，实际上MMaDA更高）。
- 在**世界知识文生图**（WISE Natural）上大幅领先（0.67），得益于长CoT推理训练。
- 在**文本推理**上，GSM8K 73.4%超越LLaDA-8B（70.7）和Dream-7B（81.0？此处Dream-7B的81.0高于MMaDA，但论文称“comparable”，实际上GSM8K上Dream-7B更高，但MMLU和MATH上MMaDA优于部分模型），整体与顶尖AR模型（Qwen2-7B）差距不大。
- **关键发现**：联合训练产生跨模态协同（图3）；UniGRPO比diff-GRPO更高效稳定；统一扩散架构可支持inpainting等扩展任务。

## 7. 优点

- **架构创新**：首次将纯离散扩散应用于统一多模态模型，避免混合损失，简化建模。
- **后训练系统化**：提出混合长CoT微调+专为扩散定制的RL算法，填补了该领域空白。
- **跨模态协同**：实验直接证明了文本推理能力提升对图像生成质量的正面影响（图3、4）。
- **效率优势**：扩散模型可并行去噪，仅需50步即可生成高质量图像，比AR模型更高效。
- **任务扩展性**：自然支持inpainting、文本补全等任务，无需额外微调。
- **开源**：代码和模型已公开，促进可重复研究。

## 8. 不足与局限

- **模型规模**：仅实验了8B参数，未探讨更大规模（如30B+）的性能，结论的泛化性受限。
- **文本数据来源**：文本预训练仅使用RefinedWeb（开源），相比LLaMA-3、Qwen-2等使用的专有或更高质量数据，可能限制文本推理上限（GSM8K上低于Dream-7B，但Dream-7B可能使用更多数学数据）。
- **RL消融单一**：RL消融主要在GSM8K数学推理上进行（图6、7），未在多模态理解或文生图任务上展示RL贡献的消融结果（表6虽含CLIP Score和ImageReward，但非RL特定对比）。
- **计算开销**：虽然UniGRPO比蒙特卡洛方法高效，但仍需要多次前向传播（每个梯度步对每个回答作一次前向），大规模训练开销仍较高。
- **样本多样性**：长CoT数据主要通过少数模型（DeepSeek-R1、GPT-4.1）生成，可能存在数据偏差，导致模型在某些边缘场景下推理僵硬。
- **公平性**：部分对比模型（如DreamLLM、Emu）在文生图或理解基准上数据缺失，无法完全公平对比所有指标；另外MMaDA可能因后训练而过拟合到奖励指标（如CLIP Score），评测时可能高估。
- **安全与偏见**：论文未讨论模型生成内容的偏见、有害内容风险或安全措施。

（完）
