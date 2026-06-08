---
title: "ChartSketcher: Reasoning with Multimodal Feedback and Reflection for Chart Understanding"
title_zh: ChartSketcher：结合多模态反馈与反思的图表推理方法
authors: "Muye Huang, Lingling Zhang, Jie Ma, Han Lai, Fangzhi Xu, Yifei Li, Wenjun Wu, Yaqiang Wu, Jun Liu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=BxRsXqjWft"
tags: ["query:mm-cot"]
score: 8.0
evidence: 面向图表的多步骤视觉推理，结合多模态反馈
tldr: 现有逐步推理模型在图表理解中无法修正源于视觉理解的错误。论文提出ChartSketcher，通过多模态反馈和反思机制，让模型在推理过程中利用视觉交互进行自我修正。该方法在图表问答任务上显著提升了准确性，特别是当视觉理解有误时。为多模态逐步推理提供了新的方向。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-bxrsxqjwft/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 844, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bxrsxqjwft/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1381, \"height\": 636, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bxrsxqjwft/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1433, \"height\": 537, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bxrsxqjwft/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1411, \"height\": 873, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bxrsxqjwft/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1378, \"height\": 814, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bxrsxqjwft/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1178, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bxrsxqjwft/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1374, \"height\": 1517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bxrsxqjwft/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 425, \"height\": 203, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bxrsxqjwft/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 550, \"height\": 722, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bxrsxqjwft/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 582, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bxrsxqjwft/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 576, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bxrsxqjwft/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 577, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-bxrsxqjwft/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 580, \"height\": 396, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-bxrsxqjwft/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 431, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bxrsxqjwft/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1457, \"height\": 1694, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bxrsxqjwft/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 458, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bxrsxqjwft/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1214, \"height\": 727, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bxrsxqjwft/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 803, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bxrsxqjwft/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 896, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bxrsxqjwft/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1196, \"height\": 174, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bxrsxqjwft/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1303, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bxrsxqjwft/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 698, \"height\": 187, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-bxrsxqjwft/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1456, \"height\": 1719, \"label\": \"Table\"}]"
motivation: 现有逐步推理模型仅聚焦文本逻辑，无法在视觉理解错误时修正推理。
method: 提出多模态反馈驱动的逐步推理方法，利用视觉交互进行自我反思和修正。
result: 在图表理解基准上取得优异表现，尤其是在视觉复杂场景下提升明显。
conclusion: 多模态反馈能有效增强逐步推理模型的视觉鲁棒性和自纠正能力。
---

## Abstract
Charts are high-density visualization carriers for complex data, serving as a crucial medium for information extraction and analysis. Automated chart understanding poses significant challenges to existing multimodal large language models (MLLMs) due to the need for precise and complex visual reasoning. Current step-by-step reasoning models primarily focus on text-based logical reasoning for chart understanding. However, they struggle to refine or correct their reasoning when errors stem from flawed visual understanding, as they lack the ability to leverage multimodal interaction for deeper comprehension. Inspired by human cognitive behavior, we propose ChartSketcher, a multimodal feedback-driven step-by-step reasoning method designed to address these limitations. ChartSketcher is a chart understanding model that employs Sketch-CoT, enabling MLLMs to annotate intermediate reasoning steps directly onto charts using a programmatic sketching library, iteratively feeding these visual annotations back into the reasoning process. This mechanism enables the model to visually ground its reasoning and refine its understanding over multiple steps. We employ a two-stage training strategy: a cold start phase to learn sketch-based reasoning patterns, followed by off-policy reinforcement learning to enhance reflection and generalization. Experiments demonstrate that ChartSketcher achieves promising performance on chart understanding benchmarks and general vision tasks, providing an interactive and interpretable approach to chart comprehension.

---

## 论文详细总结（自动生成）

# ChartSketcher 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：现有多模态大语言模型（MLLMs）在自动化图表理解中面临严峻挑战，尤其是需要复杂视觉推理的任务（如定位重叠数据点、交叉趋势线、密集数值信息）。当前逐步推理模型（如 CoT）主要依赖文本逻辑，当错误源于视觉理解时，无法利用多模态交互进行修正或细化。
- **动机**：人类在处理复杂视觉信息时，会通过绘制草图来标记和组织关键细节，将问题分解并聚焦关键区域。受此启发，作者提出 ChartSketcher，让模型在推理过程中直接在图表上绘制中间标注，并将这些视觉注释反馈给自身，从而实现稳定的逐步多模态推理和自我修正。
- **整体含义**：将多模态反馈和反思机制融入逐步推理，显著提升 MLLM 在图表理解上的视觉鲁棒性和自纠正能力，同时保持较好的通用视觉能力。

## 2. 方法论
- **核心思想**：采用 **Sketch-CoT**（草图链式推理），通过程序化草图库让 MLLM 在图表上动态绘制点、线、箭头等标记，形成“动作-感知-反思”闭环。模型每一步输出绘图代码，系统渲染新图像后反馈给模型，模型据此进行下一步推理。
- **关键技术细节**：
  - **程序化草图库**：设计轻量级绘图语言（支持点、线、圆、矩形、箭头，以及平移、旋转、删除等操作），坐标归一化到 [0,1]。
  - **草图推理流水线**：实时解析 MLLM 输出中的绘图命令，渲染图像并重新编码为视觉 token 输入下一步，形成“画图-反馈”循环，直到 no-code 结束。
  - **两阶段训练策略**：
    - **冷启动阶段（Cold Start）**：包含两部分数据合成：
      - 非反思 Sketch-CoT 数据：基于 EvoChart 图像，用种子问题增强 QA 对，通过 LLM（Qwen2.5-32B）蒸馏推理链，强制输出绘图代码。共 300K 样本。
      - 反思 Sketch-CoT 数据：在非反思数据基础上，由 LLM 故意引入坐标错误（如使用其他点的坐标），然后模仿人类反思用语（如“Oh, I made a mistake”）并修正。两部分以 1:1 混合，训练模型仅在出错时反思。
    - **强化学习阶段（RL）**：使用 **Sketch-MCTS** 算法在无标签数据上收集高质量路径。MCTS 扩展时设置去重、无效反思检测；终止条件为找到 3 个正确答案或超过 15 次模拟。从最优路径取正样本，低价值兄弟节点、渲染错误节点、重复节点作为负样本，进行 **KTO** 训练。数据来源包括 ChartQA、ChartBench、VisualCoT 等，共 50K 样本。
- **算法流程（文字描述）**：冷启动阶段先用 SFT 学习非反思推理模式，再用 RPO 损失学习反思模式；RL 阶段用 Sketch-MCTS 采样后通过 KTO 优化。推理时采用低温度、限制最大链长 12 步。

## 3. 实验设计
- **数据集**：
  - 图表专用：ChartQA-H/A、EvoChart-QA、ChartBench、PlotQA、ChartX、VisualCoT（含多个通用数据集的聚合得分）。
  - 通用视觉：OpenImages、Flickr30k、DocVQA、Visual7W、GQA、Emotic、TextVQA、TextCap、SROIE、Infographic、CUB、DUDE 等（共 18 个数据集）。
- **基准方法**：
  - 专有模型：GPT-4o、Gemini-2.0、Claude-3.5。
  - 开源 MLLM：Qwen2VL-72B/2B、QvQ-Preview-72B、InternVL2.5-78B。
  - 图表专家模型：ChartGemma-2B、ChartLlama、ChartAssistant、OneChart、ChartVLM 等。
- **评估指标**：使用 DeepSeek-Distill-Qwen-32B 评估答案正确性，3 次投票取多数。所有结果均为本地复现。

## 4. 资源与算力
- **硬件**：两个机器 —— 一个 Atlas 800T A2 和 8 × A800-40G GPU。
- **训练细节**：
  - 冷启动：LoRA（rank=16, alpha=32），batch size=64，学习率 1e-4，4 epoch 非反思 + 1 epoch RPO。
  - RL 阶段：KTO，1 epoch，LoRA rank=16，batch size=32，学习率 1e-5。
  - MCTS 参数：最大深度 8，最大子节点 3，CPUCT=3.0，模拟次数上限 15，成功找到 3 个答案后停止。
- **推理效率**：实验表明 ChartSketcher-72B 推理速度慢于 Qwen2VL 基线（需多步重新编码），但优于 QvQ-Preview（输出吞吐量更低）。

## 5. 实验数量与充分性
- **主实验**：在 5 个图表专用数据集和 13 个通用数据集上全面对比，报告了完整结果（见附录 Table 8）。
- **消融实验**：包含 5 组关键消融：
  - w/o Rethink & RL（仅冷启动非反思）
  - w/ Rethink w/o RL（有反思但用 SFT 代替 RL）
  - w/o RL（仅冷启动完整阶段）
  - w/o Feedback（推理时禁用多模态图像反馈）
  - w/o CoT（直接 SFT）
- **额外分析**：
  - 推理步骤长度和反思次数统计分析（图 3）。
  - 与 ReFocus 在 ChartQA 子集上的公平对比（Table 4）。
  - 在 ChartX 上与 ChartVLM 的对比（Table 3）。
  - 对 RL 采样策略的消融（Sketch-MCTS vs 简单拒绝采样，Table 5）。
  - 推理效率对比（Table 6）。
  - 大量案例可视化（图 4、附录 F）。
- **充分性评价**：实验设计全面，覆盖多领域、多难度、多消融维度，评价指标使用投票机制减少偏差，对比方法涵盖最先进专有和开源模型。消融实验系统验证了每个组件的贡献。

## 6. 主要结论与发现
- ChartSketcher 在图表理解基准上显著超越基线 Qwen2VL-72B，并接近/超越 GPT-4o 等专有模型（如 ChartQA-H: 85.20 vs GPT-4o 84.32）。
- 两阶段训练策略有效：冷启动后性能略低于基线（因 OOD 合成数据），但 RL 阶段大幅提升。
- Sketch-CoT 和多模态反馈是核心：去除反馈在需要复杂推理的数据集（EvoChart）上性能下降明显。
- 反思机制和 RL 训练共同提升了自纠正能力，模型在困难问题上使用更多推理步骤和反思次数。
- 模型虽然专为图表设计，但仍在通用视觉任务上保持竞争力，说明泛化能力未受损。

## 7. 优点
- **方法创新**：将“绘制草图”这一人类直觉行为引入 MLLM 推理，形成闭环视觉反馈，解决了传统文本 CoT 无法感知和修正视觉错误的问题。
- **可解释性与交互性**：推理过程可视化为中间草图，用户可直观理解模型思考步骤，且模型能主动纠正自身错误（如坐标标错后重画）。
- **训练设计精巧**：冷启动阶段通过跨模态蒸馏（LLM→MLLM）合成高质量标注数据；反思数据生成方式简单有效；RL 阶段用 Sketch-MCTS 实现步级对比学习。
- **实验全面**：涵盖大量数据集、多种消融、与相关方法（如 ReFocus）直接对比，验证了通用性和稳健性。
- **代码与数据开源**：承诺完全开源，便于后续研究。

## 8. 不足与局限
- **推理效率低**：每步需重新编码图像，导致推理速度远慢于传统模型（Table 6 显示整体速度仅为基线 Qwen2VL-72B 的 1/9）。这对实时应用构成挑战。
- **自我反思不稳定**：附录指出模型可能出现无效自我反思、过度思考、无限循环等问题，当前通过降低温度和限制链长（12步）缓解，但并非根本解决。
- **计算资源需求高**：两阶段训练需要大量 GPU 资源（8×A800-40G），且 MCTS 采样过程开销大，可能对资源有限团队不够友好。
- **应用范围有限**：当前仅支持静态 2D 图表，未扩展到 3D 图表或动态图表；虽然通用能力保持，但整体性能在某些通用数据集上仍弱于 InternVL2.5 等最新通用模型。
- **理论分析缺失**：论文承认缺乏对草图反馈循环收敛性和鲁棒性的形式化理论分析，未来需要进一步研究。
- **偏差风险**：训练数据主要来自合成图表和有限种子问题，可能无法覆盖真实世界图表的所有多样性。反思数据中的错误是人为构造的，模型能否在真实错误下同样有效迁移尚未验证。

（完）
