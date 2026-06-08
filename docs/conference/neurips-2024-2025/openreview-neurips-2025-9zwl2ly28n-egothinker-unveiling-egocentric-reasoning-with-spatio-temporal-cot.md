---
title: "EgoThinker: Unveiling Egocentric Reasoning with Spatio-Temporal CoT"
title_zh: EgoThinker：通过时空链式推理揭示第一人称推理
authors: "Baoqi Pei, Yifei Huang, Jilan Xu, Yuping He, Guo Chen, Fei Wu, Jiangmiao Pang, Yu Qiao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=9Zwl2Ly28N"
tags: ["query:mm-cot"]
score: 9.0
evidence: 面向第一人称视频的多模态链式推理
tldr: 现有多模态大模型在可见事件推理上表现优异，但缺乏对第一人称视频中隐藏意图和细粒度交互的理解。论文提出EgoThinker框架，通过时空链式推理监督和两阶段学习课程，赋予模型鲁棒的第一人称推理能力。该方法在构建的大规模QA数据集上取得显著提升，为多模态链式推理在复杂场景中的应用提供了新范式。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-9zwl2ly28n/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1412, \"height\": 1008, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9zwl2ly28n/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1448, \"height\": 574, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9zwl2ly28n/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 601, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9zwl2ly28n/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9zwl2ly28n/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1275, \"height\": 184, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9zwl2ly28n/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1317, \"height\": 182, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9zwl2ly28n/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 357, \"height\": 45, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-9zwl2ly28n/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1438, \"height\": 271, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9zwl2ly28n/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1453, \"height\": 425, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9zwl2ly28n/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 698, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9zwl2ly28n/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 699, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9zwl2ly28n/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1451, \"height\": 402, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9zwl2ly28n/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1449, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9zwl2ly28n/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 645, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9zwl2ly28n/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1019, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9zwl2ly28n/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1439, \"height\": 1550, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9zwl2ly28n/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 720, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9zwl2ly28n/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1173, \"height\": 249, \"label\": \"Table\"}]"
motivation: 多模态大模型缺乏第一人称视频推理能力，尤其是理解隐藏意图和细粒度交互。
method: 提出基于时空链式推理监督和两阶段学习课程的EgoThinker框架，并构建大规模第一人称视频数据集。
result: 在EgoRe-5M数据集上训练，模型在第一人称视频推理任务上表现显著优于基线。
conclusion: 时空链式推理能有效提升多模态模型在第一人称场景下的推理能力。
---

## Abstract
Egocentric video reasoning centers on an unobservable agent behind the camera who dynamically shapes the environment, requiring inference of hidden intentions and recognition of fine-grained interactions. This core challenge limits current multimodal large language models (MLLMs), which excel at visible event reasoning but lack embodied, first-person understanding. To bridge this gap, we introduce EgoThinker, a novel framework that endows MLLMs with robust egocentric reasoning capabilities through spatio-temporal chain-of-thought supervision and a two-stage learning curriculum. First, we introduce EgoRe-5M, a large-scale egocentric QA dataset constructed from 13M diverse egocentric video clips. This dataset features multi-minute segments annotated with detailed CoT rationales and dense hand–object grounding. Second, we employ SFT on EgoRe-5M to instill reasoning skills, followed by reinforcement fine-tuning (RFT) to further enhance spatio-temporal localization. Experimental results show that EgoThinker outperforms existing methods across multiple egocentric benchmarks, while achieving substantial improvements in fine-grained spatio-temporal localization tasks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：现有多模态大语言模型（MLLMs）在常规的三视角视频理解上表现优异，但严重缺乏**第一人称（egocentric）推理能力**。第一人称视频推理不同于常规视觉推理，需要推断摄像机背后不可见代理（agent）的隐藏意图、识别细粒度手-物体交互、并在跨越数分钟的视频中追踪因果链。
- **背景**：现有第一人称数据集（如Ego4D、EgoExo4D）主要关注动作理解，缺少显式的推理链、长时间跨度的因果标注以及细粒度时空定位数据，导致MLLMs在复杂的第一人称任务上表现不佳。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：提出 **EgoThinker** 框架，通过**时空链式推理（Spatio-Temporal CoT）监督**和**两阶段学习课程**，赋予MLLMs鲁棒的第一人称推理能力。
- **关键技术细节**：
  - **数据集 EgoRe‑5M**：
    - 从 HowTo100M 等网络视频中通过多阶段流水线（ego-vs-exo 分类、动态交互过滤）筛选出 8.7M 高质量第一人称片段，并结合 Ego4D、EPIC‑Kitchens、EgoExoLearn、EgoExo4D 共 13M 片段。
    - 自动生成四类 QA：
      - **短时感知**（1-10秒）：覆盖物体存在、属性、交互、动作推理等7类，共 2.4M 对。
      - **长时推理**（15-120秒）：涉及动作序列、时间定位、动作预测等6类，共 2.5M 对。
      - **思维链（CoT）**：通过 DeepSeek R1 生成显式的逐步推理过程，共 50K 对。
      - **细粒度接地**：手-物体空间定位（10K）+ 时间定位（56K），要求模型输出 `<think>...<answer>...` 格式。
  - **两阶段训练**：
    1. **监督微调（SFT）**：在 EgoRe‑5M 的短时、长时、CoT 子集以及通用视频/VQA 数据（共 1.5M 样本）上进行，建立基础推理和感知能力。
    2. **强化微调（RFT）**：使用 GRPO 算法在接地子集（EgoRe‑5M-FG）上进行，利用规则奖励（格式奖励 + IoU 奖励）优化模型的时空定位能力。
  - **奖励函数设计**：
    - 格式奖励 `R_format`：强制模型输出 `<think>...</think>` 和 `<answer>...</answer>`。
    - IoU 奖励 `R_oiou` / `R_tiou`：计算预测框/时间区间与真值的 IoU。
    - 总奖励 = 格式奖励 + IoU 奖励。

## 3. 实验设计：数据集 / 场景、benchmark、对比方法
- **第一人称基准**：
  - EgoTaskQA、QAEgo4D、EgoPlan、EgoSchema、EgoMCQ、ERQA、VLN‑QA
  - **RES**（新建的跨视图技能迁移基准）：从 EgoExoLearn、EgoExo4D 抽取 936 个样本，四选一匹配第一/第三人称。
- **时空接地基准**：
  - **手-物体接地**：EK‑Visor（13,000 个对象查询）
  - **时间接地**：EgoExoLearn（L1+ L2 级标注，3,000 个测试样本）
- **通用视频基准**：MVBench、Perception Test、VideoMME
- **对比方法**：LLaVA‑Video‑7B、LLaVA‑OneVision‑7B、VideoLLaMA3、VideoChat2‑HD、InternVL2‑8B、Exo2Ego‑7B、Qwen2‑VL‑7B、GPT‑4o、Grounding‑DINO 等。
- **幻觉检测**：VideoHallucer、POPE

## 4. 资源与算力
- **SFT 阶段**：32 张 A100 GPU，训练 30 小时。
- **RFT 阶段**：8 张 A100 GPU，训练 12 小时。
- 文中未明确提及总 GPU 天或内存消耗，但提供了基本配置。

## 5. 实验数量与充分性
- **主要对比实验**：在表中展示了在 7 个第一人称基准、2 个接地基准、3 个通用基准上的性能，对比了 8 种以上基线模型。
- **消融实验**：
  - 训练数据组分（Short/Long/CoT/FG）对最终性能的影响（表 5）
  - SFT vs. RFT 对比（表 6）
  - 输入帧数的影响（图 3）
  - 幻觉检测（表 7）
  - 接地数据对第一人称理解的影响（表 8）
  - 额外视频源 (HowTo100M) 的作用（表 10）
  - COCO 通用接地任务泛化（表 11）
- **充分性评价**：实验覆盖了多种任务和消融维度，结果客观，未发现人为偏袒；但缺少 error bars（可能因计算成本），对超参数敏感性分析不足。总体而言，实验设计较全面，能支撑主要结论。

## 6. 论文的主要结论与发现
- **EgoThinker 在第一人称推理、时空定位任务上均达到 SOTA**，尤其在 EgoPlan 上提升 4.4%、VLN‑QA 上提升 8.0%、RES 跨视图任务上提升 8.4%。
- **两阶段训练策略（SFT + RFT）有效**：RFT 显著提升接地精度，且不损害高层次的推理任务；单纯 SFT 在接地任务上改进有限，甚至可能损害其他任务。
- **EgoRe‑5M 各组分贡献互补**：短时数据提升基础感知；长时数据增强时序推理；CoT 数据改善记忆型 QA；接地数据增强细粒度定位。
- 模型在通用视频理解上未出现退化（MVBench +1.8%，Perception Test +2.4%），表明两阶段训练不仅解锁第一人称能力，也增强了整体视频理解。

## 7. 优点：方法或实验设计上的亮点
- **数据集规模与质量**：EgoRe‑5M 是目前最大的第一人称 QA 数据集（5M 对），包含从秒级到分钟级的多样问题，并附带显式 CoT 和精细接地标注，自动生成但经过质量抽查（95% 正确率）。
- **训练范式创新**：首次将 GRPO 应用于第一人称时空定位，通过规则奖励实现可验证的微调，避免了传统 RLHF 中奖励模型训练的不稳定性。
- **跨视图推理能力**：新建 RES 基准，证明了模型能将第三人称观察的技能迁移到第一人称场景。
- **全面评估**：不仅在第一人称任务上测评，还验证了通用视频理解和幻觉抑制，展示了鲁棒性。
- **代码与数据开源**（GitHub），便于复现和扩展。

## 8. 不足与局限
- **实验局限**：
  - 未提供 error bars 或置信区间，部分结果可能受随机性影响。
  - 消融实验未对 RFT 的超参数（如 KL 惩罚系数 β、采样数量 N）进行系统调优。
  - 主要对比模型（如 GPT‑4o、Gemini 2.5 Pro）仅在部分接地任务上定性比较，缺少定量对比。
- **应用限制**：
  - 依赖离线微调和大量标注（13M 片段 + 5M QA），无法在资源受限环境下进行实时推理。
  - 视频来源主要为 HowTo100M（指令视频），可能引入任务偏差，未充分覆盖日常打闹、社交等场景。
  - 手-物体接地仅在 EK‑Visor 上评估，该数据集为厨房场景，泛化到其他环境未知。
- **方法局限**：
  - 两阶段训练需分别切换数据集，流程复杂；未来可探索端到端联合训练。
  - 模型基于 Qwen2‑VL‑7B，更大模型（如 72B）上的性能提升潜力未完全探索（仅在第 4.1 节与 Qwen2.5‑VL‑72B 做了接地对比，未做 SFT+RFT 后对比）。
  - RLVR 奖励仅依赖格式和 IoU，缺少语义正确性奖励（如答案是否与视频内容一致），可能鼓励模型生成格式正确但推理错误的回答。
- **潜在偏差**：数据集标注自动生成，经过 LLM，可能引入 LLM 自身的偏见或虚构。

（完）
