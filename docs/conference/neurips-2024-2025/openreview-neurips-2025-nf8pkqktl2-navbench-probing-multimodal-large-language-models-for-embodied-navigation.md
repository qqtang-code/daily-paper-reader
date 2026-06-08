---
title: "NavBench: Probing Multimodal Large Language Models for Embodied Navigation"
title_zh: NavBench：探测多模态大模型的具身导航能力
authors: "Yanyuan Qiao, Haodong Hong, Wenqi Lyu, Dong An, Siqi Zhang, Yutong Xie, Xinyu Wang, Qi Wu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=nf8PKQKtl2"
tags: ["query:mm-cot"]
score: 7.0
evidence: 具身导航中的逐步执行
tldr: 该论文提出NavBench基准，用于评估多模态大模型在具身导航中的零样本能力。基准包含导航理解（3200个QA对）和逐步执行（432个场景）两个部分。通过认知任务和分层复杂度设计，揭示模型在空间认知和行动推理上的不足。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8pkqktl2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1387, \"height\": 575, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8pkqktl2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1425, \"height\": 530, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8pkqktl2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1450, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8pkqktl2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1453, \"height\": 273, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8pkqktl2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 462, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8pkqktl2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 699, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8pkqktl2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 691, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8pkqktl2/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 473, \"height\": 224, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-nf8pkqktl2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 743, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nf8pkqktl2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 710, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nf8pkqktl2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 284, \"label\": \"Table\"}]"
motivation: 多模态大模型在视觉语言任务中表现优异，但其在具身环境中的理解与行动能力尚未充分探索。
method: 构建包含导航理解和逐步执行两部分的基准，覆盖多种认知任务和复杂场景。
result: 通过零样本评估，揭示模型在全局指令对齐、时间进度估计等方面的局限性。
conclusion: 该基准为多模态大模型的具身导航能力提供了系统评估框架。
---

## Abstract
Multimodal Large Language Models (MLLMs) have demonstrated strong generalization in vision-language tasks, yet their ability to understand and act within embodied environments remains underexplored. We present NavBench, a benchmark to evaluate the embodied navigation capabilities of MLLMs under zero-shot settings. NavBench consists of two components: (1) navigation comprehension, assessed through three cognitively grounded tasks including global instruction alignment, temporal progress estimation, and local observation-action reasoning, covering 3,200 question-answer pairs; and (2) step-by-step execution in 432 episodes across 72 indoor scenes, stratified by spatial, cognitive, and execution complexity. To support real-world deployment, we introduce a pipeline that converts MLLMs' outputs into robotic actions. We evaluate both proprietary and open-source models, finding that GPT-4o performs well across tasks, while lighter open-source models succeed in simpler cases. Results also show that models with higher comprehension scores tend to achieve better execution performance. Providing map-based context improves decision accuracy, especially in medium-difficulty scenarios. However, most models struggle with temporal understanding, particularly in estimating progress during navigation, which may pose a key challenge.

---

## 论文详细总结（自动生成）

# NavBench：探测多模态大模型的具身导航能力 —— 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究背景**：多模态大语言模型（MLLMs）在静态视觉-语言任务（如视觉问答、视频理解）中展现出强大的跨模态推理和零样本泛化能力。然而，它们能否在具身环境中理解并执行任务（尤其是导航）尚未被充分探索。
- **现有 benchmarks 的局限**：传统的导航基准（如 R2R、ObjectNav）依赖任务特定的监督训练，仅以最终成功率作为评价指标，无法反映模型是否真正理解导航行为（可能通过数据集偏差或捷径到达目标）。且这些基准未区分任务难度，将所有轨迹平等对待。
- **核心问题**：MLLMs 是否真正理解具身导航行为并能够自主做出逐步决策？如何系统地评估这两种能力？
- **整体含义**：本文提出 **NavBench**，一个在零样本设置下评估 MLLMs 具身导航能力的基准。它将评估分解为 **导航理解**（global、progress、local 三个层次）和 **导航执行**（逐步决策，按空间、认知、执行复杂度划分难度），并设计了从模拟到真实世界的部署管线，以揭示模型在导航中的真实能力与不足。

## 2. 方法论

### 2.1 核心思想
- 将导航能力拆解为两个互补组件：
  - **导航理解（Navigation Comprehension）**：评估模型是否理解导航行为，包括全局指令对齐、时间进度估计、局部观测-行动推理。
  - **导航执行（Navigation Execution）**：评估模型能否在陌生环境中逐步作出正确的移动决策。
- 引入**细粒度难度分类**，基于空间、认知、执行三个维度的复杂度评分，将任务分为易、中、难三级。
- 设计**真实世界部署管线**，将 MLLM 输出转化为机器人可执行动作，验证模拟评估的可迁移性。

### 2.2 关键技术细节

#### 导航理解任务（3,200 个 QA 对）
- **全局指令对齐**（1,200 个样例）：给定一段全景轨迹和 5 个候选指令（含 1 个真实指令和 4 种干扰：基本无关、方向替换、物体替换、子指令打乱），模型需选出与轨迹匹配的指令。
- **时间进度估计**（1,000 个样例）：给定部分轨迹和完整的子指令列表，模型需预测最后完成的子指令索引。
- **局部观测-行动推理**（1,000 个样例）：两个子任务：
  - 未来观测预测：给定当前视图和动作，选出正确的下一视图。
  - 未来动作预测：给定两帧连续视图，选出导致这一变化的动作。
- 所有任务均为多项选择，答案从候选集合中选出。

#### 导航执行任务（432 个案例，72 个场景）
- 在 Matterport3D 模拟器中，以零样本方式执行逐步导航：每步模型接收全景观测、自然语言指令和候选航点，需选择下一个位置，直至到达目标。
- 难度分类公式（归一化后映射到 1–9 分，分为 Easy 1–3、Medium 4–6、Hard 7–9）：
  - **空间复杂度**：\(\Phi_{\text{spatial}} = \alpha_1 \log(1+d) + \alpha_2 \log(1+\theta) + \alpha_3 I(z>1.5) + \alpha_4 \log(1+A)\)
    - \(d\)：路径总长度；\(\theta\)：转向角标准差；\(z\)：垂直变化；\(A\)：2D 覆盖面积。
  - **认知复杂度**：\(\Phi_{\text{cognitive}} = \beta_1 \log(1+L) + \beta_2 \log(1+V) + \beta_3 \log(1+S) + \beta_4 \log(1+M) + \beta_5 C\)
    - \(L\)：指令长度；\(V\)：动词数；\(S\)：空间词数；\(M\)：地标提及数；\(C\)：从句数。
  - **执行复杂度**：\(\Phi_{\text{execution}} = \gamma_1 \log(1+N) + \gamma_2 \log(1+T) + \gamma_3 F + \gamma_4 D\)
    - \(N\)：步数；\(T\)：转弯次数；\(F\)：楼层变化指示；\(D\)：决策点数。
- 权重 \(\alpha, \beta, \gamma\) 经验设定，并通过人类评分验证。

#### 真实世界部署管线
- 包括三个模块：
  1. **航点预测模块**：使用 RGB-D 图像生成候选航点（基于 RES-50 和 Transformer）。
  2. **MLLM 决策模块**：根据导航指令选择最合适的航点（输出角度和距离）。
  3. **低级控制器**：将航点转换为机器人运动指令（相对旋转和距离）。

## 3. 实验设计

### 3.1 数据集与场景
- **数据来源**：从 R2R、RxR、GEL-R2R、FGR2R 等现有导航基准中提取指令-轨迹对，并使用 Matterport3D 模拟器渲染全景和单视图 RGB 图像。
- **理解任务**：3,200 个 QA 对，分布在全局（1,200）、进度（1,000）、局部（1,000）三个子任务。
- **执行任务**：432 个导航案例，来自 72 个独特室内场景，按难度分层（Easy/Medium/Hard）。

### 3.2 对比方法
- **闭源模型**：GPT-4o、GPT-4o-mini、Gemini-2.0-flash、o4-mini。
- **开源模型**：InternVL2.5-2B/8B、Qwen2.5-VL-3B/7B、LLaVA-OneVision-7B、LLaVA-Next-7B、Llama3.2-Vision-11B。
- **人类水平参考**：在 VLN-Bench (tiny) 上进行人工标注和评估。

### 3.3 评估指标
- **理解任务**：准确率（Accuracy）。
- **执行任务**：成功率（SR）和路径效率加权成功率（SPL）。
  \[
  \text{SPL} = \frac{1}{N}\sum_{i=1}^N S_i \cdot \frac{\ell_i}{\max(\ell_i, p_i)}
  \]
  其中 \(S_i\) 为成功指示，\(\ell_i\) 为最短路径，\(p_i\) 为实际路径长度。

## 4. 资源与算力

- 论文明确提到：开源模型使用 **vLLM** 和 **lmdeploy** 部署在单张 **NVIDIA A6000 GPU（48GB）** 上进行评估。
- 未提及训练过程（零样本评估，无需训练），因此没有训练时长或总计算量信息。
- 真实世界部署使用 **双臂复合移动机器人**，配备 **Intel RealSense D435 摄像头** 和 **水滴 2 轮式底座**，所有物理实验在室内实验室进行。
- 未给出具体运行时间或能耗数据。

## 5. 实验数量与充分性

### 主要实验
- **主表（Table 1）**：全面对比了 10 个模型（4 闭源 + 1 人类参考 + 5 开源）在理解任务（全局、进度、局部三项）和执行任务（易、中、难三级）上的性能。
- **VLN-Bench (tiny) 子集**：额外报告了 GPT-4o 和 Qwen2.5-VL-7B 在该子集上的表现，与主实验结果一致。

### 消融与深入分析
- **干扰类型分析（Figure 6）**：将全局指令对齐任务按四种干扰类型（basic、direction、object、shuffle）分解，揭示模型对空间术语和时序结构的敏感性。
- **局部观测-行动推理（Figure 7）**：分别展示未来动作预测和未来观测预测的准确率。
- **地图信息影响（Table 2）**：在 GPT-4o 上对比有无地图拓扑提示，按难度分层，发现中等难度增益最大（+4.86 百分点）。
- **Chain-of-Thought（CoT）提示（Table 3）**：对 GPT-4o 和 Qwen2.5-VL-7B 进行 CoT 实验，发现全局指令对齐提升明显，但其他任务收益微弱。
- **错误分析（Figure 8）**：手工分析 100 个失败案例，归纳出四类错误：计划错误、行动错位、过早/过晚停止、幻觉移动。
- **轨迹长度影响**：按轨迹长度分组分析进度估计错误率（短：1–2步；中：3–4步；长：5+步），发现 GPT-4o 错误率随长度大幅上升，而弱模型在所有长度上均表现不佳。
- **真实世界验证**：使用 GPT-4o 和 Qwen2.5-VL-7B 各测试 10 个案例，成功率分别为 60% 和 40%，与模拟结果趋势一致。

### 充分性与公平性
- 实验覆盖了多种主流闭源和开源模型，任务设计多样，分析角度丰富。
- 所有评估均遵循零样本协议，使用相同的指令格式和模拟器，确保了跨模型可比性。
- 不足之处：未报告误差条或统计显著性检验；未涉及模型在多轮运行下的稳定性；真实世界实验样本量较小（各 10 例）。

## 6. 主要结论与发现

1. **理解与执行紧密相关**：模型在理解任务上的整体表现与执行能力呈正相关，高理解分数通常对应更好的导航成功率。
2. **GPT-4o 综合最优**：在所有任务上表现最佳，尤其在理解全局指令和逐步执行方面。
3. **轻量开源模型潜力可观**：Qwen2.5-VL-7B 在简单任务上接近 GPT-4o-mini，具备实用部署潜力。
4. **时间推理是瓶颈**：所有模型在“时间进度估计”和“打乱子指令”条件下表现极差，表明当前 MLLMs 缺乏对导航中时序关系的理解。
5. **地图上下文辅助中等难度任务**：提供拓扑地图信息能一致提高决策准确率，中等难度场景提升最显著。
6. **CoT 帮助有限**：仅全局指令对齐受益，其他任务无提升，推测是因为导航执行本身已是逐步过程。
7. **错误模式揭示原因**：常见失败源于计划错误和进度估计失败，印证了理解任务的诊断价值。
8. **模拟与真实世界一致性**：真实世界验证结果与模拟趋势一致，支持 NavBench 作为可靠评估工具。

## 7. 优点（方法或实验设计亮点）

- **系统化能力分解**：将导航能力拆解为理解（三个层次）和执行（多难度），使评估更具诊断性，而非仅看最终成功率。
- **细粒度难度分类**：基于空间、认知、执行三维度量化复杂度，并辅以人类验证，为不同能力水平的模型提供针对性分析。
- **多维度干扰设计**：在全局指令对齐中使用四种语义不同的干扰类型，揭示模型在方向、物体、时序理解上的具体弱点。
- **可迁移性验证**：设计了从模拟到真实环境的完整部署管线，并进行了小型真机实验，增强了基准的现实相关性。
- **广泛的模型覆盖**：涵盖闭源和开源、不同参数规模的模型，结论具有普遍性。
- **深入的错误分析**：手工标注失败案例类型，并与理解任务弱点相关联，提供改进方向。

## 8. 不足与局限

- **环境多样性有限**：所有模拟数据来自 Matterport3D（室内场景），未包含室外、动态障碍物或交互式任务，可能限制泛化性。
- **缺乏统计显著性报告**：未给出误差条或置信区间，无法判断性能差异的统计可靠性。
- **真实世界实验规模小**：每模型仅测试 10 个案例，结果可靠性有限，且未涉及未知环境或复杂指令。
- **未考虑模型效率**：未比较不同模型的计算延迟、内存占用或能耗，这对实际部署至关重要。
- **零样本设置局限**：虽然零样本评估体现了泛化性，但未探索微调或 few-shot 场景下的表现提升空间。
- **未涉及多模态融合细节**：没有分析不同模型如何融合视觉与文本信息（如注意力模式），缺乏可解释性。
- **人类基线有限**：人类评估仅在 VLN-Bench (tiny) 子集上进行，规模较小，且未在所有任务上进行人类打分为基准。
- **忽视连续控制**：执行任务采用离散视角选择抽象化，未评估连续运动控制能力，这可能简化了真实机器人面临的挑战。

（完）
