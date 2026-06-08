---
title: "Open Vision Reasoner: Transferring Linguistic Cognitive Behavior for Visual Reasoning"
title_zh: 开放视觉推理器：将语言认知行为迁移到视觉推理
authors: "Yana Wei, Liang Zhao, Jianjian Sun, Kangheng Lin, jisheng yin, Jingcheng Hu, Yinmin Zhang, En Yu, Haoran Lv, Zejia Weng, Jia Wang, Qi Han, Zheng Ge, Xiangyu Zhang, Daxin Jiang, Vishal M. Patel"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=oEgybA04dY"
tags: ["query:mm-cot"]
score: 10.0
evidence: 将语言推理行为迁移到多模态推理，使用强化学习
tldr: 该研究将大语言模型通过强化学习获得的推理行为迁移到多模态大模型中。提出两阶段范式：先进行大规模语言冷启动微调，再进行近1000步的多模态强化学习。实验表明行为转移在冷启动早期即出现，而RL进一步区分视觉行为。该方法在视觉推理任务上达到开源领先水平。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-oegyba04dy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1225, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oegyba04dy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1448, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oegyba04dy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1444, \"height\": 682, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oegyba04dy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1450, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oegyba04dy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 657, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oegyba04dy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 263, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oegyba04dy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1134, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oegyba04dy/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 421, \"height\": 226, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-oegyba04dy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 522, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oegyba04dy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 536, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oegyba04dy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1448, \"height\": 1019, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oegyba04dy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1439, \"height\": 197, \"label\": \"Table\"}]"
motivation: 大语言模型的推理能力源于强化学习，但如何将该能力迁移到多模态模型尚未充分探索。
method: 基于Qwen2.5-VL-7B，先进行语言冷启动微调，再进行大规模多模态强化学习。
result: 冷启动早期即出现行为转移，RL进一步优化视觉行为，超越此前所有开源工作。
conclusion: 成功将语言推理行为迁移至多模态模型，揭示了行为转移的关键机制。
---

## Abstract
The remarkable reasoning capability of large language models (LLMs) stems from cognitive behaviors that emerge through reinforcement with verifiable rewards. This work investigates how to transfer this principle to Multimodal LLMs (MLLMs) to unlock advanced visual reasoning. We introduce a two-stage paradigm built on Qwen2.5-VL-7B: a massive linguistic cold-start fine-tuning, 
followed by multimodal reinforcement learning (RL) spanning nearly 1,000 steps—surpassing all previous open-source efforts in scale.
This pioneering work reveals three fundamental insights: 1) Behavior transfer emerges surprisingly early in cold start due to linguistic mental imagery. 2) Cold start broadly memorizes visual behaviors, while RL critically discerns and scales up effective patterns. 3) Transfer strategically favors high-utility behaviors such as visual reflection. Our resulting model, Open-Vision-Reasoner (OVR), achieves state-of-the-art performance on a suite of reasoning benchmarks, including 95.3% on MATH500, 51.8% on MathVision and 54.6% on MathVerse. We release our model, data, and training dynamics to catalyze the development of more capable, behavior-aligned multimodal reasoners.

---

## 论文详细总结（自动生成）

以下是基于论文《Open Vision Reasoner: Transferring Linguistic Cognitive Behavior for Visual Reasoning》的详细中文总结。

---

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）通过可验证奖励的强化学习（RL）能够涌现出强大的推理能力，其背后是“认知行为”（如回溯、验证、子目标分解等）的习得。然而，这种能力如何有效迁移到多模态大模型（MLLM）以解锁高级视觉推理，尚缺乏系统性研究。
- **背景**：早期多模态RL多采用RLHF（基于学习奖励模型），易受奖励篡改；近期虽出现基于规则奖励的多模态RL方法（如Perception-R1、R1-OneVision等），但未深入探究语言认知行为如何跨模态迁移。
- **核心问题**：如何将语言推理中的认知行为转移到MLLM，实现高效的视觉推理？

## 2. 方法论

- **核心思想**：采用“冷启动 + 大规模多模态强化学习”两阶段范式，先在纯语言数据上注入认知行为，再通过RL在视觉任务中激活和放大这些行为。
- **关键技术细节**：
  - **第一阶段：语言冷启动（Cold Start）**  
    - 对Qwen2.5-VL-7B的LLM模块进行监督微调（SFT），使用约200万条从DeepSeek-R1蒸馏得到的高质量推理数据（涵盖数学、科学、逻辑等）。  
    - 训练配置：5个epoch，batch size=640，序列长度64k，学习率2×10⁻⁴。
  - **第二阶段：多模态强化学习（Multimodal RL）**  
    - 基于Open-Reasoner-Zero框架，使用PPO + GAE（γ=1, λ=1），规则奖励（答案匹配即1，否则0）。  
    - 训练数据：约30万条多模态（含几何、图表、STEM等）和语言混合数据。  
    - 训练约900步，序列长度采用课程学习：2400→2470→2470（24k → 32k → 48k）。  
    - 策略和评论家网络独立更新，无KL正则或熵奖励。
- **算法流程**：  
  1. 输入图像和文本提示，策略πθ生成n条轨迹。  
  2. 计算GAE优势函数ˆAt。  
  3. 通过截断的PPO目标更新策略，同时最小化评论家损失。  
  4. 最终模型对多个代表性中间检查点进行均匀平均。

## 3. 实验设计

- **测试基准**：
  - **语言推理**：AIME 2024/2025、MATH500、GPQA Diamond、MMLU、MMLU-Pro。
  - **多模态推理**：MathVista、MathVision、MathVerse、DynaMath、WeMath、LogicVista、MMMU-Pro、CharXiv。
  - **感知能力**：MMBench、BLINK、MMStar、HallusionBench、POPE、RealWorldQA、MME、MMVet。
- **对比方法**：
  - 开源SFT方法：LLaVA-OneVision-7B、InternVL3-8B、Qwen2.5-VL-7B等。
  - 开源RL方法：OpenVLThinker、MM-Eureka、ReVisual-R1、VL-Rethinker、R1-OneVision等。
  - 闭源模型：Gemini-2.0-Flash、Claude 3.7 Sonnet、GPT-4o、Doubao-1.5-vision-pro-32k等。
- **额外分析**：使用GPT-4o自动检测四种视觉认知行为（视觉反思、分治、视觉验证、目标驱动视觉追踪）的涌现率，并计算从语言到视觉的迁移率。

## 4. 资源与算力

- 论文未明确给出总GPU小时数或具体集群规模，仅说明所有实验在NVIDIA A100 Tensor Core GPU上进行。RL阶段共900步，冷启动5个epoch，文本中未进一步披露算力消耗细节。

## 5. 实验数量与充分性

- **实验数量**：在8个语言/多模态推理基准和8个感知基准上进行了评估，并额外设计了认知行为分析（4类行为）和训练动态可视化。
- **充分性与公平性**：对比了当前几乎所有主流开源MLLM（7B级别）及部分更大模型和闭源模型，消融实验覆盖了冷启动与RL阶段的效果差异。但未报告多次运行的标准差或置信区间，可能存在单次运行偏差。
- **总体评价**：实验较为充分，对比全面，但缺少统计显著性分析；感知部分的消融分析相对简略。

## 6. 主要结论与发现

1. **行为转移在冷启动早期即出现**：由于语言推理数据中包含“心理意象”（如“让我可视化...”），冷启动后模型迅速将语言行为泛化到视觉任务上。
2. **冷启动广泛学习，RL批判性选择**：冷启动阶段模型记忆了大量模式，而RL则像“过滤器”一样放大高效行为、抑制低效行为。
3. **转移策略性选择高效用行为**：如“视觉反思”的迁移率高于“视觉验证”，因为回溯类行为在多模态任务中更基础、更受RL青睐。
4. **感知能力先降后升**：语言冷启动导致感知退化（如幻觉增加），但多模态RL能够有效恢复，甚至在某些基准上超越基座模型。
5. **RL在纯感知任务上扩展性有限**：在OCR、计数等任务上，奖励上升但回答长度不增长，表明缺乏核心视觉认知行为限制了可扩展性。

## 7. 优点

- **系统性研究**：首次严格分析了语言到视觉的认知行为迁移机制，并定义了四种视觉认知行为及量化指标。
- **大规模开源实践**：基于Qwen2.5-VL-7B，是当前该模型上最大的开源RL实践（900步，30万混合数据）。
- **性能领先**：OVR-7B在多模态推理基准上全面超越之前开源模型，甚至在AIME 2024/2025上接近或超越更大参数模型。
- **训练动态透明**：公开训练曲线、行为涌现率、性能演化，有助于社区理解RL如何影响认知行为。
- **社区贡献**：计划开源模型、数据和训练动态，推动可复现研究。

## 8. 不足与局限

- **感知退化问题**：冷启动导致视觉幻觉增加，虽然RL部分恢复，但未完全消除，且未提出有效缓解策略（仅建议未来将语言数据融入预训练）。
- **外部有效性**：实验仅基于Qwen2.5-VL-7B一个模型，结论是否泛化到其他架构（如LLaVA、InternVL）未验证。
- **缺乏因果分析**：仅发现行为与性能之间的相关性，未通过干预实验证明因果关系（如删除某行为后性能变化）。
- **统计稳健性不足**：未报告多次运行的误差棒，部分基准可能受单次生成随机性影响。
- **感知任务扩展性局限**：在OCR、计数等纯感知任务上，RL扩展性不佳，提示现有行为组合可能缺失更原始的视觉认知能力（如多轮工具使用、心理旋转等）。
- **应用限制**：模型仅7B参数，在更复杂、开放域视觉推理任务上的能力仍有限；冷启动需要大量蒸馏数据，成本较高。

---

（完）
