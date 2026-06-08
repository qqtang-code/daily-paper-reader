---
title: "SAM-R1: Leveraging SAM for Reward Feedback in Multimodal Segmentation via Reinforcement Learning"
title_zh: SAM-R1：利用SAM进行强化学习下的多模态分割奖励反馈
authors: "Jiaqi Huang, Zunnan Xu, Jun Zhou, Ting Liu, Yicheng Xiao, Mingwen Ou, Bowen Ji, Xiu Li, Kehong Yuan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=dHOSTp8MBl"
tags: ["query:mm-cot"]
score: 7.0
evidence: 通过强化学习实现多模态细粒度推理
tldr: 论文指出当前多模态分割依赖带推理过程的人工标注数据，成本高昂。为此提出SAM-R1框架，结合SAM分割模型与强化学习，让多模态大模型在图像分割任务中进行细粒度推理，无需人工推理标注。实验表明该框架有效提升了分割中的推理能力，为多模态推理训练提供了新范式。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-dhostp8mbl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1430, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dhostp8mbl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1446, \"height\": 579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dhostp8mbl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 1189, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dhostp8mbl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1452, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dhostp8mbl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1444, \"height\": 631, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-dhostp8mbl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 920, \"height\": 509, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dhostp8mbl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1032, \"height\": 393, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dhostp8mbl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1457, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dhostp8mbl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1442, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dhostp8mbl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 605, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dhostp8mbl/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1209, \"height\": 293, \"label\": \"Table\"}]"
motivation: 现有方法依赖人工标注推理过程，成本高且难以扩展，因此需要无需推理标注的多模态推理框架。
method: 提出SAM-R1框架，将SAM集成到强化学习流程中，利用分割掩码作为奖励信号，引导模型生成推理过程。
result: 在图像分割任务中验证了框架有效性，模型能生成合理推理并提升分割精度。
conclusion: 证明了无需推理标注即可训练多模态模型的推理能力，为降低标注成本开辟新路径。
---

## Abstract
Leveraging multimodal large models for image segmentation has become a prominent research direction. However, existing approaches typically rely heavily on manually annotated datasets that include explicit reasoning processes, which are costly and time-consuming to produce. Recent advances suggest that reinforcement learning (RL) can endow large models with reasoning capabilities without requiring such reasoning-annotated data. In this paper, we propose SAM-R1, a novel framework that enables multimodal large models to perform fine-grained reasoning in image understanding tasks. Our approach is the first to incorporate fine-grained segmentation settings during the training of multimodal reasoning models. By integrating task-specific, fine-grained rewards with a tailored optimization objective, we further enhance the model's reasoning and segmentation alignment. We also leverage the Segment Anything Model (SAM) as a strong and flexible reward provider to guide the learning process. With only 3k training samples, SAM-R1 achieves strong performance across multiple benchmarks, demonstrating the effectiveness of reinforcement learning in equipping multimodal models with segmentation-oriented reasoning capabilities.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将严格按照您的要求，对论文《SAM-R1: Leveraging SAM for Reward Feedback in Multimodal Segmentation via Reinforcement Learning》进行结构化、深入的分析总结。

---

### 论文核心分析：SAM-R1

#### 1. 核心问题与整体含义

*   **研究动机：** 多模态大模型在图像分割领域，特别是需要复杂推理的“推理分割”任务上展现出巨大潜力。然而，现有方法（如 LISA）通常依赖于大量带有显式推理过程的人工标注数据集，这使得数据收集成本高昂、耗时耗力，且模型容易过拟合，泛化到新领域的能力受限。
*   **核心问题：** 如何在不依赖昂贵的人工推理标注数据的前提下，训练多模态大模型，使其具备在图像分割任务中进行细粒度、强逻辑推理的能力？
*   **整体含义：** 本文旨在验证一种新的训练范式：通过强化学习，利用分割模型自身的输出作为奖励信号，来驱动多模态大模型自主进化出推理能力，从而摆脱对显式推理标注的依赖，实现更高效、更通用的多模态推理分割。

#### 2. 方法论：SAM-R1框架

*   **核心思想：** 将强大的分割模型 **SAM** 集成到多模态大语言模型（**MLLM**）的强化学习训练循环中，作为“奖励提供者”而非仅仅是一个下游分割模块。通过设计基于分割质量的精细化奖励函数，引导 MLLM 生成更高水平的推理过程和更精准的分割提示。

*   **关键技术细节：**
    1.  **架构设计：** 框架由 MLLM（如 Qwen2.5VL-7B）和 SAM 两部分组成。MLLM 接收图像和用户问题，首先生成包含 `<\think>` 标签的推理过程（Chain-of-Thought），然后生成包含 `<\answer>` 标签的结构化答案（包括边界框坐标、关键点坐标等）。这些结构化输出作为提示输入给 SAM，用于生成最终的分割掩码。
    2.  **强化学习算法（改进的 GRPO）：** 基于 **GRPO**（组相对策略优化）进行改进：
        *   **非对称裁剪阈值：** 在损失函数中，将 PPO 中标准的对称裁剪阈值替换为不对称的 `ε_low` 和 `ε_high`。通过提高 `ε_high` 的值，赋予模型更大的自由度来探索高优势动作，鼓励更精细的优化。
        *   **Token级损失归一化：** 针对 GRPO 可能产生冗长但信息密度低的答案，将所有 token 的损失进行归一化，使每个 token 都受到相同的惩罚。这有助于抑制模型生成冗余输出，提高推理效率。

    3.  **精细化奖励函数设计：**
        *   **分层分割精度奖励：** 将 SAM 作为奖励提供者，计算预测掩码与真实掩码之间的 IoU，并根据 IoU 值给予不同等级的奖励（如 4, 3, 2, 0 分）。这种分级奖励比单一阈值奖励更精细，能引导模型逐步提升精度。
        *   **推理格式奖励：** 奖励那些输出严格遵循 `<\think>` 和 `<\answer>` 标签格式的推理链。
        *   **分割格式奖励：** 奖励模型所输出的边界框和关键点符合预定义的 JSON 格式。

*   **优化目标：** 论文提出了改进后的损失函数 `J_ours(θ)`，其核心是组合了非对称裁剪的优势函数项和KL散度惩罚项。

#### 3. 实验设计

*   **使用数据集：**
    *   **训练集：** 从 RefCOCOg 的训练集中随机抽取了 3000 个样本。
    *   **In-domain（领域内）测试：** RefCOCOg 的官方测试集。
    *   **Out-of-domain（跨领域/零样本）测试：** 包括 RefCOCO testA, RefCOCO+ testA, 以及更具挑战性的 ReasonSeg 数据集。
*   **Benchmark/评价指标：** 主要采用 **gIoU**（全局IoU平均值）和 **cIoU**（累积IoU）作为分割精度评价指标。此外，也在 LISA-Grounding 基准上测试了模型的指代理解能力。
*   **对比方法：**
    *   在 ReasonSeg 上，对比了 **OVSeg**, **ReLA**, **Grounded-SAM**, **LISA-7B/13B**, **SAM4MLLM**, 以及 **Seg-Zero-7B**。
    *   在 RefCOCO 系列数据集上，对比了 **LAVT**, **ReLA**, **LISA-7B**, **PixelLM-7B**, **PerceptionGPT-7B**, 以及 **Seg-Zero-7B**。

#### 4. 资源与算力

*   **明确说明：** 论文在“Experimental Setup”部分明确指出，所有实验均在 **8 × A100 GPU** 上完成。
*   **未明确说明：** 论文没有提及具体的训练总时长（如多少小时或轮次），也未说明是否需要分布式训练或其他并行策略。但给定其 3000 样本的小训练集规模和 8卡配置，可推断训练相对快速。

#### 5. 实验数量与充分性

*   **实验数量：** 论文共设计了 **6 组核心实验**，外加一些可视化和失败案例分析。
    1.  **ReasonSeg 零样本分割：** 对比多个主流方法，证明了在零样本推理分割任务上的 SOTA 性能。
    2.  **指代分割：** 在 RefCOCO/+/g 三个标准基准上对比，展示了在域内和域外数据上的竞争力。
    3.  **消融实验：** 针对**阈值策略**（固定阈值 vs. 分层阈值）和**算法组件**（Token级约束、非对称裁剪）进行了详细消融。
    4.  **数据效率分析：** 对比了使用 3k 和 10k 训练样本的效果，验证了小样本下的有效性。
    5.  **泛化能力测试：** 在 LISA-Grounding 基准上测试了模型的指代理解能力，展示其泛化性。
    6.  **可视化分析：** 展示了成功和失败的推理及分割案例。
*   **充分性与公平性：**
    *   **充分性：** 实验设计较为充分，涵盖了主要任务、核心消融、数据效率和泛化性分析。特别是数据效率分析，直观地展示了方法优势。
    *   **客观性与公平性：**
        *   论文指出 Seg-Zero 的报告结果无法复现（“Seg-Zero-7B*”），采用其提供权重进行测试，这种做法是严谨的。
        *   与 LISA 等方法相比，SAM-R1 的方法在“资源投入”（小样本训练）和“性能产出”（零样本/域外表现）之间有非常公平且优势明显的对比。
        *   消融实验设计得比较好，清晰地证明了每个改进点（分层IoU、非对称裁剪、Token级归一化）的单独和联合贡献。

#### 6. 主要结论与发现

1.  **高性能：** 仅使用 **3000个训练样本**，SAM-R1 就在多个基准上取得了领先或极具竞争力的成绩，尤其在零样本的 ReasonSeg 基准上显著超越了依赖于大量监督数据的 LISA 等基线模型。
2.  **数据效率：** 增加训练数据量至 10k 并未带来显著的性能提升，表明模型在 3k 样本时已基本达到性能饱和，验证了其极高的数据效率。
3.  **方法有效性：** 设计的每一个组件（分层奖励、非对称裁剪、Token级损失）都单独和共同地对最终性能带来了正向增益，证明了方法论的有效性。
4.  **泛化能力：** 模型不仅在分割任务上表现优异，在指代理解任务（REC）上也展现了强大的零样本泛化能力，这得益于强化学习训练带来的推理能力提升。

#### 7. 优点

*   **方法创新性：** 首次将 SAM 作为强化学习的“奖励提供者”而非下游模块，使分割模型的精确反馈直接驱动推理模型的学习，这是一个有见地的设计。
*   **数据效率：** 仅需 3k 样本即可取得 SOTA 效果，显著降低了对大规模、高质量标注数据的依赖，具有很高的实用价值和工程友好性。
*   **算法改进：** 在 GRPO 基础上进行的“非对称裁剪”和“Token级损失”改进是实用且有效的优化，解决了 RL 训练中探索不足和冗余输出的问题。
*   **分析详尽：** 论文不仅报告了成功的案例，还专门用一节分析了失败案例（分割不完整、过分割、无法生成有意义的负点），这种对方法局限性的坦诚剖析（如附录 A.2 和 A.3）是高质量研究的体现。
*   **迁移性强：** 模型在分割之外的 REC 任务上也展现零样本能力，证明了其推理能力的泛化性。

#### 8. 不足与局限

*   **SAM 参数冻结：** SAM 作为奖励提供者被冻结，其与 MLLM 之间是单向信息流。论文作者也指出，未来工作是联合优化二者，以形成协同进化。
*   **缺乏判别性负样本：** 模型无法自动生成有意义的负参考点（区分“非目标”区域）。尽管作者尝试通过奖励机制引导，但最终失败，这被识别为当前框架的一个**根本性局限**，可能限制其在需要精细区分类似物体场景下的表现。
*   **实验覆盖度有限：** 虽然实验比较充分，但主要聚焦于自然场景图像的指代分割。其方法在更复杂的领域，如医学图像分割、自动驾驶中的视觉推理等，适用性未经验证。
*   **计算资源：** 虽训练样本少，但训练使用 8 张 A100 显卡，对个人或小型实验室的门槛不算低。
*   **推理过程质量：** 虽然模型生成了推理链，但可视化案例显示，有时正确的语义推理并未能完美转化为精准的像素级掩码。模型在学习“如何推理”上表现良好，但在“将推理结果精确落地为分割”方面仍有提升空间。

（完）
