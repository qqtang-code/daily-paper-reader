---
title: Counterfactual Evolution of Multimodal Datasets via Visual Programming
title_zh: 通过视觉程序实现多模态数据集的反事实演化
authors: "Minghe Gao, Zhongqi Yue, Wenjie Yan, Yihao Hu, Wei Ji, Siliang Tang, Jun Xiao, Tat-Seng Chua, Yueting Zhuang, Juncheng Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=bTRH1O5Bp2"
tags: ["query:mm-cot"]
score: 8.0
evidence: 通过反事实演化生成推理复杂度可控的多模态数据集
tldr: 针对多模态数据集多样性不足且推理复杂度不可控的问题，提出SCOPE框架，利用符号化视觉程序引导反事实演化，沿推理路径、视觉上下文等轴进行干预，生成推理步骤丰富且可验证的样本，为多模态逐步推理研究提供高质量数据。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-btrh1o5bp2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btrh1o5bp2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btrh1o5bp2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1444, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btrh1o5bp2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1438, \"height\": 588, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btrh1o5bp2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 765, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btrh1o5bp2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 746, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btrh1o5bp2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 691, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btrh1o5bp2/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1226, \"height\": 659, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btrh1o5bp2/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1224, \"height\": 661, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btrh1o5bp2/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 727, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-btrh1o5bp2/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 730, \"height\": 495, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-btrh1o5bp2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1429, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btrh1o5bp2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1437, \"height\": 529, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btrh1o5bp2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 467, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btrh1o5bp2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 685, \"height\": 356, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btrh1o5bp2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 736, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btrh1o5bp2/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 746, \"height\": 475, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-btrh1o5bp2/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1069, \"height\": 394, \"label\": \"Table\"}]"
motivation: 现有多模态数据集增强方法缺乏对样本推理复杂度的可控性。
method: 提出SCOPE框架，结合反事实推理和符号化视觉程序来演化数据集。
result: 生成的样本在推理多样性和复杂度上显著优于现有方法。
conclusion: SCOPE为多模态逐步推理任务提供了灵活的数据生成工具。
---

## Abstract
The rapid development of Multimodal Large Language Models (MLLMs) poses increasing demands on the diversity and complexity of multimodal datasets. Yet manual annotation pipelines can no longer keep pace. Existing augmentation methods often follow fixed rules and lack verifiable control over sample diversity and reasoning complexity. To address this, we introduce Scalable COunterfactual Program Evolution (SCOPE), a framework that uses symbolic Visual Programming to guide program evolution via counterfactual reasoning. SCOPE performs the three steps of counterfactual inference: (1) Abduction, by generating verifiable programs to model reasoning associations; (2) Action, by intervening on program structure along three axes—reasoning path, visual context, and cross-instance composition; and (3) Prediction, by categorizing evolved instances by difficulty, structure, and input multiplicity. Based on this process, we build SCOPE-Train and SCOPE-Test, evolving benchmarks with expert validation. To support training, we propose MAP, a curriculum learning strategy that aligns model capacity with sample difficulty. Experiments show that SCOPE improves reasoning performance, exposes model blind spots, and enhances visual dialog capabilities.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：现有多模态数据集增强方法（如基于大模型的提示转换、模板增强、场景图分解）存在缺乏可验证性、难以控制推理复杂度、多样性有限等缺陷，无法满足多模态大模型（MLLMs）对数据多样性、可扩展性及推理复杂度的迫切需求。
- **整体含义**：本文旨在构建一个可验证、可控制的多模态数据集演化框架，通过符号化的视觉程序（Visual Programming）和反事实推理，系统性地生成多样化、推理层次清晰的样本，为MLLMs的鲁棒训练与细粒度诊断提供支撑。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：提出 **SCOPE（Scalable COunterfactual Program Evolution）** 框架，利用视觉编程将图像-问题-答案三元组转化为可执行的Python代码，然后通过反事实推理的三个步骤（Abduction、Action、Prediction）对代码进行结构化干预，生成演化样本。同时设计了 **MAP（Memory and Attention Path）** 课程学习策略，按难度渐进式训练模型。
- **关键技术细节**：
  - **Verifiable Abduction（可验证溯因）**：用代码生成器（如GPT-4o）将输入图像与问题转化为可执行程序 `z = π(x, q)`，执行后若输出与标准答案一致则保留，形成四元组 `(q, x, z, a)`。
  - **Controllable Action（可控干预）**：沿三个轴进行程序干预：
    - **推理路径扩展**：在程序中插入/嵌套原子函数（如 `find`, `verify_property`）增加推理深度或宽度。
    - **视觉上下文编辑**：利用 SAM 对图像中实体进行替换、改变或删除，保持程序结构不变，增加视觉变化。
    - **跨实例组合**：将来自不同图像/数据源的问题与代码组合，实现多图像或跨域推理。
  - **Evolving Prediction（演化预测分类）**：对演化后的程序进行三方面分析：
    - **推理难度**：采用 Halstead effort 公式 `E = D × V` 计算复杂度，并设阈值（4000、6000）分出 easy/medium/hard。
    - **结构变化**：将程序表示为有向无环图（DAG），根据深度/宽度扩展因子分为 depth、width、balanced。
    - **输入多样性**：记录输入图像数量（single/dual/multi）。
  - **MAP 课程学习**：按难度排序（先易后难），并引入记忆分支（depth任务）、并行注意力分支（width任务）及门控函数，同时使用归一化 Halstead effort 作为损失权重，动态调整样本贡献。

### 3. 实验设计：数据集、基准、对比方法
- **数据集**：从六个公开 VQA 数据集（SEED-Bench2、MME、MMBench、GQA、OK-VQA、TallyQA）共 14,874 个样本出发，经过三轮演化构建 **SCOPE-Train**（31,233 样本）和 **SCOPE-Test**（13,389 样本），并由领域专家验证高接受率（91%-96%）。
- **基准**：采用 MMVet、RealWorldQA、MMBench test、SeedBench2-Plus、MuirBench、MMT val、POPE 等通用与专项基准；视觉对话任务使用 ConvBench、ContextVD、VisDial。
- **对比方法**：
  - **Provision**（基于场景图子图抽取）
  - **VLB**（基于模板改写问题与编辑图像）
  - **SCOPE**（本文方法）
  - **基线模型**：GPT-4o、LLaVA-1.5-13B、DeepSeek-VL-7B、Phi-3.5-Vision-4B，以及训练中使用的 Qwen2.5-VL-7B、InternVL-2.5-2B。
- **评估指标**：准确率（Accuracy），并分解到难度、结构、输入多样性三个维度。

### 4. 资源与算力
- 论文中 **未明确说明** 使用的 GPU 型号、数量及训练时长。仅提及使用 GPT-4o 进行程序生成，模型训练在 Qwen2.5-VL-7B 和 InternVL-2.5-2B 上进行，但具体计算资源细节缺失。

### 5. 实验数量与充分性
- **实验数量**：文章报告了多组实验，包括：
  - 在 SCOPE-Test 上对多个 MLLM 的细粒度评估（表2）
  - 在通用基准上对比三种演化方法（表3）
  - 视觉对话任务评估（表4）
  - 消融实验：扩展方法组合（表6）、MAP 各组件（表5）、演化轮次影响（图6）
- **充分性与公平性**：实验覆盖多种模型规模（2B、4B、7B、13B、GPT-4o），对比方法包含代表性结构化增强方案，且在多个基准上评估，保证了比较的全面性。同时指出 SCOPE 数据与测试基准无重叠，避免数据泄露。但未提供统计显著性检验或误差棒，且缺乏对更大模型（如 70B 级别）的验证。

### 6. 论文的主要结论与发现
- SCOPE-Test 揭示了现有 MLLM 在 hard 难度、宽度型推理及多图像推理上的系统性盲点。
- SCOPE-Train 能显著提升模型在多个基准上的推理能力，且收益随模型规模增大而增加。
- MAP 课程学习进一步提升了训练效率，尤其在视觉对话任务中表现出色。
- 消融实验表明推理路径扩展贡献最大，多个扩展策略存在协同效应；MAP 中 gating 模块和 difficulty-aware loss 是关键组件。
- 三轮演化后性能趋于饱和，权衡计算成本后选择三轮。

### 7. 优点：方法或实验设计上的亮点
- **可验证性与可控性**：通过符号化程序替代黑箱自然语言，实现可追踪、可验证的推理链路，并支持精确干预推理复杂度。
- **系统性的反事实演化**：从推理路径、视觉上下文、跨实例组合三个维度进行结构化扩展，覆盖了多种数据多样性需求。
- **课程学习对齐**：MAP 策略与 SCOPE 的难度分层自然契合，自动调度样本并引入难度加权，提升训练效率。
- **可扩展性**：框架不依赖固定模板或场景图，可推广至更多视觉任务（如指令生成、视频推理），且开源工具支持社区二次演化。

### 8. 不足与局限
- **算力资源未报告**：缺失 GPU 型号、数量、训练时长等关键信息，影响可复现性。
- **数据源有限**：仅基于六个公开数据集，虽宣称框架通用，但未在更多领域（如医疗、遥感）验证。
- **结构变化排序启发式**：MAP 中将 width 视为比 depth 更难，仅基于经验假设，缺乏理论或实验支持。
- **无统计显著性检验**：核心结果未报告置信区间或 P 值，可能削弱结论的统计可靠性。
- **人类评估规模有限**：每轮仅抽样 1000 实例，总接受率虽高，但未提供细粒度错误分析或跨类别可靠性。
- **模型规模覆盖欠深**：未测试 13B 以上更大模型的性能增益，结论的泛化范围有限。
- **三轮演化截断**：性能在第三轮后趋于平稳，但未说明更多轮次是否会产生过拟合或数据污染。

（完）
