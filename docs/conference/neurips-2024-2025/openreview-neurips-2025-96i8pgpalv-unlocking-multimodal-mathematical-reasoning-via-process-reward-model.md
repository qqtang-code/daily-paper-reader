---
title: Unlocking Multimodal Mathematical Reasoning via Process Reward Model
title_zh: 通过过程奖励模型解锁多模态数学推理
authors: "Ruilin Luo, Zhuofan Zheng, Lei Wang, Yifan Wang, Xinzhe Ni, Zicheng Lin, Songtao Jiang, Yiyao Yu, Chufan Shi, Ruihang Chu, Jin zeng, Yujiu Yang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=96I8PGPALv"
tags: ["query:mm-cot"]
score: 9.0
evidence: 使用过程奖励模型进行多模态数学推理
tldr: 过程奖励模型（PRM）在纯文本数学推理中表现优异，但在多模态领域尚未探索。本文首次将PRM应用于多模态数学推理，识别了三个关键挑战：高质量多模态推理数据稀缺、缺乏自动化过程标注方法、以及单模态PRM的局限。通过提出解决方案，该方法提升了多模态大模型在数学推理中的测试时扩展和强化学习能力。该工作拓展了PRM在多模态推理中的应用边界。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1374, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1219, \"height\": 563, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 895, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1447, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1447, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 521, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1421, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 630, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1340, \"height\": 707, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 258, \"height\": 192, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 501, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 247, \"height\": 184, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 238, \"height\": 168, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 66, \"height\": 62, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 371, \"height\": 251, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-96i8pgpalv/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 421, \"height\": 322, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 288, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1456, \"height\": 985, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 304, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1376, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1369, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1449, \"height\": 673, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1231, \"height\": 479, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1082, \"height\": 1173, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1452, \"height\": 812, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1167, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1390, \"height\": 333, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1389, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1019, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1176, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1308, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 542, \"height\": 623, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-96i8pgpalv/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 475, \"height\": 429, \"label\": \"Table\"}]"
motivation: 多模态数学推理中过程奖励模型的应用尚属空白，存在数据、标注和模态适配难题。
method: 提出将过程奖励模型引入多模态大模型，并解决数据稀缺和自动化标注问题。
result: 在多个多模态数学推理基准上取得了显著性能提升。
conclusion: PRM可有效嵌入多模态推理流程，增强复杂推理能力。
---

## Abstract
Process Reward Models (PRMs) have shown promise in enhancing the mathematical reasoning capabilities of Large Language Models (LLMs) through Test-Time Scaling (TTS). However, their integration into multimodal reasoning remains largely unexplored. In this work, we take the first step toward unlocking the potential of PRMs in multimodal mathematical reasoning. We identify three key challenges: (i) the scarcity of high-quality reasoning data constrains the capabilities of foundation Multimodal Large Language Models (MLLMs), which imposes further limitations on the upper bounds of TTS and reinforcement learning (RL); (ii) a lack of automated methods for process labeling within multimodal contexts persists; (iii) the employment of process rewards in unimodal RL faces issues like reward hacking, which may extend to multimodal scenarios. To address these issues, we introduce URSA, a three-stage Unfolding multimodal pRocess-Supervision Aided training framework. We first construct MMathCoT-1M, a high-quality large-scale multimodal Chain-of-Thought (CoT) reasoning dataset, to build a stronger math reasoning foundation MLLM, URSA-8B. Subsequently, we go through an automatic process to synthesize process supervision data, which emphasizes both logical correctness and perceptual consistency. We introduce DualMath-1.1M to facilitate the training of URSA-8B-RM. Finally, we propose Process-Supervised Group-Relative-Policy-Optimization (PS-GRPO), pioneering a multimodal PRM-aided online RL method that outperforms vanilla GRPO. With PS-GRPO application, URSA-8B-PS-GRPO outperforms Gemma3-12B and GPT-4o by 8.4% and 2.7% on average across 6 benchmarks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

过程奖励模型（PRM）在纯文本大语言模型的数学推理中已展现出提升测试时扩展（TTS）和强化学习（RL）效果的潜力，但在多模态数学推理领域尚未被探索。本文首次尝试将PRM集成到多模态大语言模型（MLLM）的数学推理中，识别出三大关键挑战：

- **高质量推理数据稀缺**：现有MLLM缺乏大规模、高质量的多模态思维链（CoT）推理数据，限制了TTS和RL的上限。
- **自动化过程标注方法缺失**：多模态场景下的过程标注不仅需要逻辑正确性，还需考虑视觉-文本一致性（感知一致性），而当前缺乏自动化手段。
- **单模态PRM的局限**：在RL中直接使用标量过程奖励易导致奖励黑客和长度偏差问题，且这些风险在多模态场景下可能加剧。

论文整体目标：提出一套三阶段训练框架URSA，系统性构建和应用多模态PRM，以解锁多模态数学推理能力。

## 2. 方法论：核心思想、关键技术细节、算法流程

### 总体框架：URSA三阶段

**阶段一：数学密集型对齐与指令微调**

- **构建高质量CoT推理数据集 MMathCoT-1M**：从MathV360K、Multimath、MAVIS、Geo170K、VarsityTutors等开源数据中收集143万样本，按解答类型分为三类：仅答案型、分析格式型、CoT格式型。分别采用CoT扩展、重写、格式统一三种策略，利用Gemini-1.5-Flash-002合成高质量CoT轨迹，并过滤不一致样本。
- **训练基础模型URSA-8B**：采用LLaVA-like架构（混合视觉编码器SAM-B+SigLIP-L + LLM骨干Qwen2.5-Math-Instruct），先进行860K数学密集型视觉-语言对齐（训练MLP projector），再在MMathCoT-1M上全参数指令微调，得到更强推理基础模型。

**阶段二：双视角过程监督数据合成**

- **二元错误定位引擎（BEL）**：收集URSA-8B零样本推理产生的约553K错误解答，用蒙特卡洛树搜索（MCTS）标注首个错误步骤。采用二分查找优化（Algorithm 1）：对每个解答，检查中间步骤的mc值（随机rollouts得到正确答案的比例），若>0则错误在后半段，否则在前半段。加入180K正确解答（全部标记为正确），共得到773K标注数据SBEL。
- **误读插入引擎（MIE）**：针对多模态特有的感知不一致问题，自动插入幻觉信息。分三步：提取图像数学信息 → 在正确解答中修改易混淆条件 → 基于错误条件继续推理并自动给后续步骤标记负标签。生成约302K样本SMIE。
- **训练PRM（URSA-8B-RM）**：合并SBEL和SMIE得到DualMath-1.1M，以每个步骤的二分类正确性为训练目标（公式4）。PRM基于URSA-8B训练。

**阶段三：将多模态PRM集成到在线RL**

- **问题发现**：在GRPO中直接使用标量过程奖励（Variant 1: 平均过程奖励+结果奖励；Variant 2: 步骤级过程奖励+结果奖励）均导致奖励黑客和长度偏差——模型倾向于产生更短、更保守的推理，测试准确率反而低于普通GRPO。
- **核心洞察**：虽然标量过程奖励在在线RL中不可靠，但PRM在BoN选择（Best-of-N）和错误识别（drop-moment检测）方面的相对质量判断是可信的。drop-moment定义为连续步骤奖励的最大相对下降（公式5），当下降超过阈值ρ时表示PRM质疑了前面步骤的有效性。
- **PS-GRPO算法**（Algorithm 2）：不再使用标量过程奖励，而是将过程监督转化为对结果正确但推理过程有drop-moment的rollout施加惩罚（公式6）。具体：若结果正确且δip < ρ，奖励为1；若结果正确但δip ≥ ρ，奖励为1-γ；否则奖励为0。然后基于组内奖励归一化计算优势（公式7），采用GRPO的优化目标（公式8）。这既区分了结果正确rollout的学习价值，又避免了PRM的长度偏差影响。

## 3. 实验设计

### 基准数据集（6个）

- **MathVerse** (testmini) – 数学推理文本/视觉变体
- **MathVision** (full set) – 多学科视觉数学
- **MathVista** (GPS子集) – 几何问题求解
- **WE-MATH** (testmini) – 复合问题分解
- **DynaMath** (testmini) – 鲁棒性动态评估
- **GeoQA** (full set) – 几何问答

### 对比方法

- **闭源MLLM**：GPT-4o、GPT-4o-mini、Gemini-1.5-pro
- **开源通用MLLM**：InternVL系列、LLaVA-OneVision、Gemma3-12B、Qwen2-VL等
- **开源数学推理MLLM**：AtomThink-EMOVA、InfiMM-Math、MAVIS、MathGLM-Vision、LlamaV-o1、Adora、MM-Eureka、OpenVLThinker、R1-Onevision等
- **TTS对比**：Self-Consistency、InternVL2.5-8B作为ORM（结果奖励模型）

### 主要实验

- **主结果（Table 1）**：URSA-8B-PS-GRPO在6个基准平均58.2%，超过Gemma3-12B（49.8%）8.4%，超过GPT-4o（55.5%）2.7%。
- **BoN评估（Table 2）**：URSA-8B-RM作为验证器，在N=4/8/16/32下均优于Self-Consistency和ORM基线，且能泛化到AtomThink-EMOVA。
- **各阶段贡献（Figure 6(b)）**：MMathCoT-1M贡献最大绝对增益，PS-GRPO在WE-MATH和MathVerse上分别带来13.2%和11.4%的相对提升。
- **消融实验（Table 3）**：DualMath-1.1M中的BEL和MIE两部分均贡献正面效果，BEL影响更大。
- **敏感性分析（Table 4）**：对PS-GRPO超参数γ（惩罚幅度）和ρ（drop-moment阈值）进行测试，γ在0.3-0.7范围内较好，ρ过小或过大均不利。
- **PS-GRPO vs PRM集成基线（Table 5）**：PS-GRPO优于Variant 1、Variant 2和DeepSeek提出的DS-GRPO方法。
- **泛化验证（Appendix C.4, Figure 8）**：MMathCoT-1M和PS-GRPO在InternVL2.5-8B和MultiMath上均有显著提升。
- **数据规模定律（Appendix C.2）**：不同比例MMathCoT-1M训练显示性能随数据量增长。
- **合成策略消融（Appendix E.1, Figure 9）**：CoT扩展、重写、格式统一各有贡献。

## 4. 资源与算力

论文在Appendix G.2中明确说明：

- **硬件**：默认使用32×NVIDIA H100-HBM3 GPU（分布式训练框架FSDP）。
- **阶段一**：VL对齐~3.5小时，指令微调~11小时。
- **阶段二**：数据对生成（16张H100，~28小时），二元错误定位（16张H100，~20小时），PRM训练（32张H100，~12小时）。
- **阶段三**：PS-GRPO训练（32张H100，~18小时）。
- **合成数据API**：使用Gemini-1.5-Flash-002进行约270万次API调用（因其成本效益高）。

## 5. 实验数量与充分性

- **主实验**：1个综合对比表（6个基准，超过15个基线模型）。
- **消融实验**：至少8组（各阶段贡献、数据策略、数据比例、PS-GRPO超参数、BEL/MIE贡献、PS-GRPO vs其他RL变体、泛化验证、合成策略消融）。
- **TTS评估**：3个基准上的BoN（N=4/8/16/32），对比Self-Consistency和ORM。
- **过程分析**：包括奖励曲线、响应长度、测试准确率随训练步数变化（Figure 4-5）。
- **充分性评价**：实验覆盖全面，既包括与领先闭源/开源模型的对比，又有细致的消融和分析。公平性较好：未使用MathVision等作为训练集（排除部分基线），所有基线采用零样本推理。但未报告误差棒（论文解释因实验成本高，但固定了随机种子）。总体而言，实验设计和数量足以支撑主要结论。

## 6. 主要结论与发现

1. **多模态PRM的首个有效应用**：首次将过程奖励模型成功应用于多模态数学推理，验证了其提升TTS和在线RL的潜力。
2. **数据的重要性**：大规模高质量CoT推理数据（MMathCoT-1M）是基础模型能力提升的关键，且表现出训练时扩展定律。
3. **双视角过程标注的有效性**：BEL（逻辑正确性）和MIE（视觉感知一致性）均能提升PRM质量，其中BEL影响更大。
4. **过程作为结果奖励更可靠**：PS-GRPO通过惩罚“结果正确但过程可疑”的rollout，有效缓解了奖励黑客和长度偏差，优于直接使用标量过程奖励的变体。
5. **SOTA性能**：URSA-8B-PS-GRPO以8B参数量在6个基准上平均超越Gemma3-12B 8.4%和GPT-4o 2.7%，并在MathVision上首次超越GPT-4o（31.5 vs 30.4）。

## 7. 优点

- **首次系统性探索**：填补了PRM在多模态推理中的空白，揭示了独特挑战与解决方案。
- **自动化标注创新**：同时考虑逻辑和视觉一致性的双引擎标注方法，降低了人工成本。
- **RL方法改进**：PS-GRPO提出了一种简单的软性惩罚机制，避免了复杂且不稳定的标量奖励建模，实验证明有效。
- **全面的开源贡献**：开源MMathCoT-1M、DualMath-1.1M、模型权重和代码，便于社区复现和进一步研究。
- **实验设计严谨**：包含与大模型(如GPT-4o)的公平对比，消融实验覆盖多维度，验证了每个组件的必要性。
- **泛化验证**：在InternVL2.5-8B和MultiMath上验证了方法的可迁移性。

## 8. 不足与局限

- **计算资源需求高**：需要大量GPU（32×H100）和API调用，可能限制了一些研究团体的复现。
- **任务范围有限**：主要聚焦于STEM（数学）推理，在更通用的视觉推理（如常识推理、科学图表）中的表现尚未验证。
- **自动化标注的质量**：虽然使用了Gemini-1.5-Flash进行合成和过滤，但仍可能存在噪声和偏差，特别是MIE引入的错误可能不完全自然。
- **RL训练稳定性**：PS-GRPO对超参数γ和ρ较为敏感（Table 4），需要调优；没有引入其他优化技巧（如动态采样、自适应KL）以确保与vanilla GRPO的公平对比，可能未达到最佳性能。
- **未报告统计显著性**：没有提供误差棒或置信区间，尽管固定了随机种子，但单次运行结果可能受随机性影响。
- **可能的风险**：依赖外部MLLM进行数据合成，如果合成器存在系统偏差，可能被放大。同时，模型能力的提升可能带来误导性依赖（如过度信任数学解题能力）。

（完）
