---
title: "Video-of-Thought: Step-by-Step Video Reasoning from Perception to Cognition"
title_zh: 视频思维：从感知到认知的逐步视频推理
authors: "Hao Fei, Shengqiong Wu, Wei Ji, Hanwang Zhang, Meishan Zhang, Mong-Li Lee, Wynne Hsu"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=fO31YAyNbI"
tags: ["query:mm-cot"]
score: 9.0
evidence: 多模态视频逐步推理，融合链式思维
tldr: 现有视频理解难以实现深度推理，缺乏细粒度时空感知和认知级场景理解。本文先提出MotionEpic多模态模型，通过时空场景图实现像素级视频定位。在此基础上开发视频思维(VoT)推理框架，继承链式思维核心，将复杂任务分解为从感知到认知的逐步推理。在视频推理基准上，VoT显著提升了性能。该工作为视频理解提供了多步推理新范式。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 851, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 849, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 847, \"height\": 781, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 842, \"height\": 317, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 841, \"height\": 246, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 846, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 841, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 844, \"height\": 270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 855, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 864, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1787, \"height\": 163, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 835, \"height\": 216, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 85, \"height\": 66, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 86, \"height\": 68, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 87, \"height\": 67, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1762, \"height\": 202, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1770, \"height\": 137, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-fo31yaynbi/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1782, \"height\": 132, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-fo31yaynbi/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 905, \"height\": 644, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-fo31yaynbi/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 882, \"height\": 603, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-fo31yaynbi/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 817, \"height\": 703, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-fo31yaynbi/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 857, \"height\": 664, \"label\": \"Table\"}]"
motivation: 视频理解缺乏细粒度时空感知和认知级推理。
method: 提出MotionEpic模型实现像素级时空定位，并构建VoT链式推理框架。
result: 在视频推理任务上取得显著性能提升。
conclusion: 逐步推理链可有效提升视频理解深度。
---

## Abstract
Existing research of video understanding still struggles to achieve in-depth comprehension and reasoning in complex videos, primarily due to the under-exploration of two key bottlenecks: fine-grained spatial-temporal perceptive understanding and cognitive-level video scene comprehension. This paper bridges the gap by presenting a novel solution. We first introduce a novel video Multimodal Large Language Model (MLLM), MotionEpic, which achieves fine-grained pixel-level spatial-temporal video grounding by integrating video spatial-temporal scene graph (STSG) representation. Building upon MotionEpic, we then develop a Video-of-Thought (VoT) reasoning framework. VoT inherits the Chain-of-Thought (CoT) core, breaking down a complex task into simpler and manageable sub-problems, and addressing them step-by-step from a low-level pixel perception to high-level cognitive interpretation. Extensive experiments across various complex video QA benchmarks demonstrate that our overall framework strikingly boosts existing state-of-the-art. To our knowledge, this is the first attempt at successfully implementing the CoT technique for achieving human-level video reasoning, where we show great potential in extending it to a wider range of video understanding scenarios. Systems and codes will be open later.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：当前视频理解模型在处理复杂视频时，难以实现深度推理，主要受限于两个瓶颈：**细粒度时空感知理解不足**（大多停留在实例或帧级分析）和**认知级视频场景理解缺失**（缺乏常识推理和因果想象能力）。
- **研究动机**：人类视频推理遵循从低级像素感知到高级认知解释的多步过程（例如先定位目标、跟踪轨迹、理解行为、结合常识形成答案）。然而，现有视频多模态大语言模型（MLLM）和链式思维（CoT）技术尚未有效结合用于视频场景。
- **整体含义**：本文首次提出面向视频的链式思维推理框架 **Video-of-Thought (VoT)**，旨在实现类人的逐步视频推理，从感知到认知层层递进。

#### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：将复杂视频推理任务分解为一系列从低到高的子问题，逐步求解。为此，先构建一个支持细粒度时空定位的视频MLLM——**MotionEpic**，再在其上搭建 **VoT** 推理框架。
- **关键技术细节**：
  - **MotionEpic 架构**：
    - 基于 Vicuna-7B LLM，使用 ViT-L/14 视频编码器和 Q-Former 投影器。
    - 引入**视频时空场景图 (STSG)** 表示：对每帧提取对象、边界框、谓词关系，并添加时序共指边（跨帧相同对象链接）。
    - 使用**循环图 Transformer** 编码 STSG，支持输入/输出 STSG。
    - **细粒度定位调优**：设计 5 类训练目标（L1-L5），涵盖粗粒度（视频-STSG配对、全图生成）和细粒度（给定动作/对象/边界框输出对应轨迹或描述），分阶段进行预训练（WebVid）、定位调优（Action Genome + WebVid子集）和指令调优（VideoChat、Video-ChatGPT数据）。
  - **VoT 推理框架**（5步链）：
    1. **任务定义与目标识别**：从问题中提取需关注的目标对象。
    2. **对象跟踪**：利用 STSG 输出目标对象的时空轨迹（部分 STSG），作为低级证据。
    3. **动作分析**：结合 STSG 中目标及其邻居节点，并注入常识知识，描述动作行为及含义。
    4. **问答排名**：对每个候选答案（或对开放式问题生成多个候选）用1-10分评估合理性，排序选最优。
    5. **答案验证**：从像素级感知和常识认知两个角度验证答案一致性，如有矛盾则重选。
- **技术特色**：STSG 既能精准定位又能减轻幻觉；VoT 未使用简单“一步步思考”提示，而是显式分解任务，并加入验证机制。

#### 3. 实验设计：数据集、基准、对比方法
- **数据集**：
  - **微调设置**：6个复杂视频QA数据集：VLEP、STAR（含4个子集）、IntentQA、Social-IQ、Causal-VidQA（含4种问题类型）、NExT-QA（含C/T/D子集）。
  - **零样本设置**：MSR-VTT、ActivityNet、NExT-QA、STAR（部分）。
  - **定位调优数据**：Action Genome（10K 手动标注 STSG） + WebVid-10M 子集（350K 视频经解析器自动标注 STSG）。
- **基准**：各数据集官方划分与评估标准（主要指标为准确率）。
- **对比方法**：
  - 传统 SoTA：InternVideo、LLaMA-VQA、VLAP、SeViLA、TranSTR、HiTeA 等。
  - 现有视频 MLLM：Video-LLaMA、VideoChat、Video-ChatGPT、Video-LLaVA、VideoChat2。
  - 消融变体：Video-LLaVA + CoT、Video-LLaVA + STSG、MotionEpic + CoT、VoT（MotionEpic）等。

#### 4. 资源与算力
- 论文明确说明：“All trainings are conducted on 16 NVIDIA A100 GPUs”，未提及训练时长。训练涉及多阶段（预训练、定位调优、指令调优），但具体耗时未给出。

#### 5. 实验数量与充分性
- **实验数量**：共呈现 4 张主表（Table 1-4）、3 张分析图（Fig 5-7）及若干消融/可视化。
  - Table 1-3：微调结果（覆盖 6 个数据集，含子集）；Table 4：零样本结果（4 个数据集）。
  - Fig 5：MotionEpic 在 STSG 解析任务上的性能（对比专用解析器与人类）。
  - Fig 6：消融 5 种调优目标（L1-L5）对零样本性能的影响。
  - Fig 7：人类评估与错误类型分析（6类错误）；案例可视化展示。
  - 附录还提供了更多定性案例（Fig 9-10）。
- **充分性与公平性**：
  - 实验覆盖了多种复杂视频推理场景（因果、反事实、社交、意图等），且对比了当时主流方法。
  - 消融实验系统分析了各组件贡献；零样本设置测试了泛化能力。
  - 但未报告方差或置信区间，也未对比参数量相近的非 MLLM 方法（如纯视觉 transformer）。总体而言，实验设计较为全面，结论可信。

#### 6. 论文的主要结论与发现
- **性能提升**：VoT（MotionEpic）在几乎所有视频QA基准上显著超越所有 SoTA，微调与零样本场景皆如此。例如 NExT-QA 上从 75.5%（VLAP）提升至 76.0%（VoT）。
- **STSG 重要性**：显式集成 STSG（如 Video-LLaVA+STSG）能提升性能，但 MotionEpic 的隐式集成更优。
- **VoT 优于简单 CoT**：对比 Video-LLaVA+CoT 与 MotionEpic+VoT，后者大幅领先，证明分解式多步推理的有效性。
- **验证机制关键**：零样本实验中去除感知或认知验证环节均导致性能下降，复杂任务两者都重要。
- **接近人类水平**：在人工评估样本（Causal-VidQA 和 Social-IQ）中，VoT 准确率接近人类，错误率显著低于基线，尤其在动作语义和常识理解上。

#### 7. 优点：方法或实验设计上的亮点
- **方法创新**：
  - 首次将 CoT 应用于视频推理，并设计了从感知到认知的显式步骤链。
  - MotionEpic 通过 STSG 实现了像素级时空定位，同时支持 STSG 的生成与理解，从而在推理中提供可解释的低级证据。
  - 引入验证机制（感知+认知双重检查）提升鲁棒性。
- **实验设计**：
  - 覆盖多种难度与类型的视频QA数据集，包括需要反事实预测、意图理解等高级认知能力的数据集。
  - 消融实验细致（L1-L5、验证子项），明确各组件贡献。
  - 进行人工评估以验证模型是否真正达到类人推理。
  - 零样本测试展示了泛化能力。

#### 8. 不足与局限
- **实验局限**：
  - 未在更多样化场景（如长视频、多轮对话、交互式任务）中评估。
  - 未与参数量更大的模型（如 GPT-4V）直接对比零样本性能（仅对比了较小 MLLM）。
  - 未讨论不同采样率（8 fps）是否最优的消融（虽有初步实验但未展示详细数据）。
- **方法局限**：
  - 依赖 STSG 标注数据（Action Genome）进行定位调优，数据获取成本高；自动标注的 WebVid 子集可能含噪声。
  - 框架较为复杂（5步链 + 验证），推理时延和计算开销较大（需多次调用 MLLM）。
  - 对开放式问题，需先让模型生成多个候选答案，可能引入额外误差。
  - 结果报告中没有不确定性评估（如多次运行标准差），可能掩盖单次运行波动。
- **社会影响**（论文已提及）：大模型训练能源消耗大；框架可能被恶意利用（如生成误导性视频解释），需许可证管理。

（完）
