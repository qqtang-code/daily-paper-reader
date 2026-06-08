---
title: "Actial: Activate Spatial Reasoning Ability of Multimodal Large Language Models"
title_zh: Actial：激活多模态大模型的空间推理能力
authors: "Xiaoyu Zhan, Wenxuan Huang, Hao Sun, Xinyu Fu, Changfeng Ma, Shaosheng Cao, Bohan Jia, Shaohui Lin, Zhenfei Yin, LEI BAI, Wanli Ouyang, Yuanqi Li, Jie Guo, Yanwen Guo"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=jquTBzt3Av"
tags: ["query:mm-cot"]
score: 7.0
evidence: 通过视角学习进行多步空间推理
tldr: 该论文提出视角学习任务，旨在提升多模态大模型的3D空间推理能力。构建了包含10万对图像-问答对的Viewpoint-100K数据集。采用两阶段微调方法，在跨视角一致性任务上取得改进。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-jqutbzt3av/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1396, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jqutbzt3av/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1435, \"height\": 813, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jqutbzt3av/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1392, \"height\": 802, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jqutbzt3av/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1389, \"height\": 762, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jqutbzt3av/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1386, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jqutbzt3av/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1378, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jqutbzt3av/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1301, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jqutbzt3av/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 288, \"height\": 1037, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-jqutbzt3av/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1387, \"height\": 663, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jqutbzt3av/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1437, \"height\": 239, \"label\": \"Table\"}]"
motivation: 多模态大模型在2D视觉上表现良好，但3D空间推理中的跨视角一致性仍有挑战。
method: 设计视角学习任务和数据集，采用两阶段微调激活空间推理。
result: 在跨视角一致性任务上取得显著提升。
conclusion: 两阶段微调能有效增强多模态大模型的空间推理能力。
---

## Abstract
Recent advances in Multimodal Large Language Models (MLLMs) have significantly improved 2D visual understanding, prompting interest in their application to complex 3D reasoning tasks. However, it remains unclear whether these models can effectively capture the detailed spatial information required for robust real-world performance, especially cross-view consistency, a key requirement for accurate 3D reasoning. Considering this issue, we introduce Viewpoint Learning, a task designed to evaluate and improve the spatial reasoning capabilities of MLLMs. We present the Viewpoint-100K dataset, consisting of 100K object-centric image pairs with diverse viewpoints and corresponding question-answer pairs. Our approach employs a two-stage fine-tuning strategy: first, foundational knowledge is injected to the baseline MLLM via Supervised Fine-Tuning (SFT) on Viewpoint-100K, resulting in significant improvements across multiple tasks; second, generalization is enhanced through Reinforcement Learning using the Group Relative Policy Optimization (GRPO) algorithm on a broader set of questions. Additionally, we introduce a hybrid cold-start initialization method designed to simultaneously learn viewpoint representations and maintain coherent reasoning thinking. Experimental results show that our approach significantly activates the spatial reasoning ability of MLLM, improving performance on both in-domain and out-of-domain reasoning tasks. Our findings highlight the value of developing foundational spatial skills in MLLMs, supporting future progress in robotics, autonomous systems, and 3D scene understanding.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，以下是对给定论文《Actial: Activate Spatial Reasoning Ability of Multimodal Large Language Models》的结构化、深入、客观的总结。

---

### 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：当前多模态大语言模型（MLLMs）在2D视觉理解上表现出色，但其是否真正具备进行复杂3D空间推理所需的精细空间信息捕捉能力，尤其是 **跨视角一致性（cross-view consistency）** 这一关键能力，仍然是一个悬而未决的问题。论文指出，现有MLLMs主要依赖于2D连续性（如视频帧间的像素变化）而非真正的3D一致性（如物体在三维空间中的几何属性保持不变）进行推理，这限制了其在现实3D场景中的鲁棒性。
- **研究动机**：作者认为，MLLMs的视觉空间智能尚未被充分激活，原因在于不恰当的数据利用方式。关键在于教会模型理解“多视角图像和视频是3D物体在2D平面上的投影”这一概念，而不是将其视为像素的简单序列。为了探索如何有效利用现有数据，教会MLLMs在3D空间中进行推理和解决问题，是一个极具价值的研究方向。
- **整体含义**：本文旨在通过专门的训练策略，激活MLLM中潜在的、但未被充分利用的空间推理能力，从而弥合2D视觉理解与鲁棒3D空间推理之间的鸿沟，对机器人、自动驾驶、3D场景理解等领域的未来进展具有重要价值。

### 2. 提出的方法论

- **核心思想**：提出**视角学习（Viewpoint Learning）** 这一基础性任务，通过让模型学习从不同视角观察同一物体时，其视点（相机位姿）如何变化，来迫使模型从依赖2D线索转向理解3D空间的一致性。核心方法是一种**两阶段微调策略**。
- **关键技术细节**：
    1.  **第一阶段：基础知识注入**
        - **数据集**：在作者贡献的Viewpoint-100K数据集上进行**监督微调（SFT）**。该数据集包含10万个自动生成的、以物体为中心的图像对，以及对应的问答对，主要包含三种问题类型：
            - 自我中心相机平移（Ego-centric Translation）
            - 自我中心相机旋转（Ego-centric Rotation）
            - 物体中心相机平移（Object-centric Translation）
        - **混合冷启动初始化（Hybrid Cold-Start Initialization）**：为了解决SFT后模型的指令遵循和思维连贯性受损问题，引入了此方法。它包括：
            - 使用Gemini 2.5 Pro生成少量高质量的伪CoT（Chain-of-Thought）数据。
            - 将这些伪CoT数据与Viewpoint-100K数据按10%和90%的比例混合，作为SFT的输入。这样模型可以同时学习视角知识并保持连贯的推理思考过程。
    2.  **第二阶段：泛化增强**
        - **算法**：在SFT后的模型基础上，使用**组相对策略优化（GRPO）** 强化学习算法进行微调。
        - **数据集**：使用SAT（Spatial Aptitude Training）数据集，该数据集是用于评估静态和动态空间推理的合成数据集。
        - **目标**：通过奖励驱动的方式鼓励模型自主生成推理链并应用第一阶段学到的空间知识，从而将基础视角任务的知识迁移到更抽象、更复杂的空间推理挑战中，提升模型的泛化能力。

- **算法流程（文字说明）**：
    1.  基于MVImgNet生成Viewpoint-100K图像对和对应QA。
    2.  **阶段1（SFT）**：使用混合冷启动初始化（90% Viewpoint-100K数据 + 10% 伪CoT数据）对基座模型（Qwen2.5-VL-7B-Instruct）进行监督微调，注入基础视角知识。
    3.  **阶段2（RL）**：加载阶段1得到的模型，使用GRPO算法在SAT数据集上进行强化学习微调，通过奖励函数（格式奖励+结果奖励）优化模型，提升其在更广泛空间任务上的泛化能力。
    4.  最终得到具备激活空间推理能力的模型Actial-7B。

### 3. 实验设计

- **使用的数据集**：
    - **训练集**：Viewpoint-100K（用于第一阶段SFT），SAT（用于第二阶段GRPO）。
    - **评估基准**：使用 **3DSRBench**、**CV-Bench** 和 **BLINK** 作为主要评估基准，全面考察模型的空间推理能力。还使用了 **MMSI-Bench** 进行额外的泛化性评估。
- **Benchmark**：
    - **3DSRBench**：评估3D空间推理（高度、位置、方向、多视角等）。
    - **CV-Bench**：评估视觉空间任务（相对位置、计数、深度等）。
    - **BLINK**：评估视觉感知和推理（多视角、相对深度、空间关系等）。
- **对比的方法**：与多种先进模型进行比较，包括：
    - **商业闭源模型**：GPT-4o, Gemini系列, QwenVLMax等。
    - **开源模型**：Robopoint-13B, LLaVA系列, Cambrian-8B等。
    - **与基座模型对比**：以 Qwen2.5-VL-7B-Instruct 为基线。

### 4. 资源与算力

- 论文在实验设置部分详细说明了训练参数，但**未明确说明具体的GPU型号、数量及总训练时长**。
- 提供的算力相关细节包括：
    - SFT阶段：2个epoch，学习率5e-6，批次大小128，50个预热步。
    - GRPO阶段：150步，学习率1e-6，批次大小1024，每个输入采样16个样本。
    - 生成限制：最大4K token。
- 结论：**论文未明确披露所用的精确算力资源**。

### 5. 实验数量与充分性

- **实验数量**：论文进行了大量且充分的实验。
    - **主要基准评估**：在3DSRBench、CV-Bench、BLINK三个主流基准上进行了全面评估，报告了多个子任务的得分。
    - **消融实验**：系统地进行了消融实验，分别分析了**去掉知识注入（w/o K.I.）** 和**去掉泛化增强（w/o G.E.）** 后的模型性能，验证了每个阶段的有效性。
    - **额外实验**：在Viewpoint-100K测试集上比较了人类表现、基座模型和微调后模型的准确率。还使用**MMSI-Bench**进行更复杂的评估。
    - **训练过程分析**：展示了GRPO阶段响应长度变化和KL散度变化，以及SFT阶段的训练损失曲线，提供了训练动态的洞察。
- **充分性与公平性**：
    - 实验设计较为充分，覆盖了域内和域外测试。
    - 对比了多个具有竞争力的基线模型，包括不同规模的开源和闭源模型。
    - 消融实验设计合理，清晰地展示了各组件贡献。
    - 公平性较好，遵循了基准的官方评估协议（如使用VLMEvalKit工具）。

### 6. 主要结论与发现

1.  **视角学习有效**：通过Viewpoint-100K数据集的SFT，能有效激活MLLM的空间推理能力，模型在多项空间任务上（包括域外任务）获得提升，表明基础视角知识的重要性。
2.  **两阶段策略有效**：知识注入（SFT）和泛化增强（GRPO）两阶段相互配合。SFT为模型打下基础，但可能导致过拟合；而GRPO有助于保留了已获得的知识并提升了泛化能力，尤其是在更广泛的任务上。
3.  **混合冷启动初始化重要**：该方法成功解决了SFT后模型推理思考能力受损的问题，使得模型能同时学习视角知识和保持连贯推理。
4.  **模型潜力巨大**：实验证明，尽管当前MLLMs在预训练中主要接触2D数据，但它们具备学习3D空间感知的巨大潜力。经过针对性训练，可以从“随机猜测”水平提升到“专家”水平（如在BLINK的多视角子任务上达到99.2%）。

### 7. 优点

- **问题定义清晰且基础**：将复杂的三维空间推理问题巧妙简化为“视角学习”这一基础任务，降低了MLLMs理解和学习3D空间的门槛，方法论具有启发性。
- **数据集自动生成**：Viewpoint-100K数据集利用现有的MVImgNet的真实世界数据和相机参数自动生成，成本低、规模大、带有精确的标注（相机相对位姿），可扩展性强。
- **两阶段训练策略设计精巧**：先注入知识，再使用强化学习增强泛化，最后通过混合冷启动初始化技术保护了模型的推理能力，各环节逻辑清晰，形成闭环。
- **实验结果有说服力**：在多个标准基准上超越了基线及多种先进模型，尤其是在CV-Bench上表现突出，甚至在BLINK的“多视角”子任务上达到了近乎完美的99.2%。广泛的消融实验有力地证明了各组件设计的有效性。

### 8. 不足与局限

- **数据集的简化与局限性**：论文自身承认，Viewpoint-100K的数据场景相对受限，所有数据都基于以物体为中心的图像，且问题仅限于水平方向的平移和旋转。这简化了真实世界多样、复杂的问题（如6自由度相机姿态估计）。未涵盖复杂的场景理解和动态交互。
- **任务形式的简化**：将问题抽象成简单的多项选择题，虽然降低了难度，但可能无法完全捕获模型在更细粒度、连续数值（如精确的姿态回归）上的空间理解能力。
- **泛化增强机制的分析**：实验显示，GRPO阶段可能会对第一阶段已习得的某些特定知识（如对高度的理解）产生负面影响。这表明基于结果奖励的优化仍可能在一定程度上与基础知识产生冲突，需要更精细的奖励函数设计或训练策略。
- **伪CoT的生成与影响**：生成的伪CoT可能包含与正确答案或“正确3D知识”相矛盾的分析。虽然作者通过控制占比（10%）来降低风险，但这仍然是潜在的不稳定性来源。
- **计算资源未详述**：论文未提供完整的计算资源消耗报告，包括使用的GPU型号、数量和总训练时长，这在一定程度上影响了实验的可重复性评估。

（完）
