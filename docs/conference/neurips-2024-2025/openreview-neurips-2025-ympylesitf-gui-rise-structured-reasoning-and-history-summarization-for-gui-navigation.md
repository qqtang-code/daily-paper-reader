---
title: "GUI-Rise: Structured Reasoning and History Summarization for GUI Navigation"
title_zh: GUI-Rise：用于GUI导航的结构化推理与历史总结
authors: "Tao Liu, Chongyu Wang, Rongjie Li, Yingchen Yu, Xuming He, Song Bai"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=YMPYLesItf"
tags: ["query:mm-cot"]
score: 8.0
evidence: 链式推理与动作预测集成
tldr: 该论文提出GUI-Rise框架，将结构化链式推理（CoT）与动作预测和历史总结集成，用于GUI导航代理。通过监督微调和强化学习（GRPO）训练，在跨域泛化上取得提升。CoT分析包括进度估计和决策推理。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ympylesitf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1402, \"height\": 761, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ympylesitf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1456, \"height\": 713, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ympylesitf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1443, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ympylesitf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ympylesitf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 449, \"height\": 451, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ympylesitf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 454, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ympylesitf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1437, \"height\": 793, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ympylesitf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1428, \"height\": 795, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ympylesitf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1456, \"height\": 747, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ympylesitf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1316, \"height\": 742, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ympylesitf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1210, \"height\": 331, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ympylesitf/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1245, \"height\": 327, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ympylesitf/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1459, \"height\": 1315, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ympylesitf/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1450, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ympylesitf/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1315, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ympylesitf/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1380, \"height\": 370, \"label\": \"Table\"}]"
motivation: 当前GUI导航代理在跨域泛化和历史利用上存在局限。
method: 集成结构化CoT推理、动作预测和历史总结，并使用GRPO进行强化学习。
result: 在多个GUI导航基准上取得跨域泛化性能提升。
conclusion: 结构化推理和强化学习有效增强了GUI代理的泛化能力。
---

## Abstract
While Multimodal Large Language Models (MLLMs) have advanced GUI navigation agents, current approaches face limitations in cross-domain generalization and effective history utilization. We present a reasoning-enhanced framework that systematically integrates structured reasoning, action prediction, and history summarization. The structured reasoning component generates coherent Chain-of-Thought analyses combining progress estimation and decision reasoning, which inform both immediate action predictions and compact history summaries for future steps. Based on this framework, we train a GUI agent, GUI-Rise, through supervised fine-tuning on pseudo-labeled trajectories and reinforcement learning with Group Relative Policy Optimization (GRPO). This framework employs specialized rewards, including a history-aware objective, directly linking summary quality to subsequent action performance. Comprehensive evaluations on standard benchmarks demonstrate state-of-the-art results under identical training data conditions, with particularly strong performance in out-of-domain scenarios. These findings validate our framework's ability to maintain robust reasoning and generalization across diverse GUI navigation tasks.

---

## 论文详细总结（自动生成）

# GUI-Rise：用于GUI导航的结构化推理与历史总结——论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题背景**：多模态大语言模型（MLLMs）推动了GUI导航智能体的发展，但现有方法在**跨域泛化**和**历史信息有效利用**方面存在局限。许多方法依赖封闭源LLM的提示工程（如GPT-4），难以适应新领域；监督微调（SFT）虽然提升分布内准确率，但容易过拟合，泛化能力弱。
- **核心挑战**：GUI导航需要长期、顺序推理，智能体必须持续追踪界面状态变化并结合自身历史做出决策。现有的历史编码方式要么只记录动作序列（缺乏视觉状态），要么使用全屏截图（计算开销大，上下文窗口受限），导致历史信息丢失和决策不准确。
- **论文目标**：提出一种**推理增强框架**，将结构化推理、动作预测和历史总结系统性地集成，训练一个名为**GUI-Rise**的GUI智能体，提升跨域泛化能力和长期任务执行的一致性。

## 2. 方法论：核心思想、关键技术细节

### 2.1 核心思想

- 在每个交互步骤，智能体执行三个子任务：
  1. **结构化推理**：输出链式思维（CoT），包括**进度估计**（Progress Estimation）和**决策推理**（Decision Reasoning）。
  2. **动作预测**：基于推理结果预测可执行的结构化动作（类型、值、坐标）。
  3. **历史总结**：将当前观察、之前历史和指令压缩为简洁文本摘要，用于后续步骤。

### 2.2 关键技术细节

- **智能体架构**：采用MLLM（基于Qwen-VL系列），输入为当前截图、用户指令和历史摘要，输出为CoT轨迹、更新的历史摘要和动作。
- **两阶段训练策略**：
  - **阶段一：冷启动训练（Cold-start Training）**  
    使用更强的MLLM（GPT-4o-mini）生成伪标签（历史摘要和结构化CoT），通过**监督微调（SFT）** 对模型进行初始化训练，学习基本推理和总结能力。损失为标准交叉熵。
  - **阶段二：强化学习（RL）**  
    采用**Group Relative Policy Optimization (GRPO)**，去掉值网络，通过组内比较计算优势。设计三种互补奖励函数：
    - **格式奖励（Format Reward, Rf）**：检查输出是否严格遵循预定义的XML标签顺序（<Progress Estimation>...<Decision Reasoning>...<Action>...<Memory Summary>...）。
    - **动作奖励（Action Reward, Ra）**：综合评估动作的结构格式匹配、动作类型正确性和坐标落在目标元素边界框内的情况。
    - **历史总结奖励（History Summary Reward, Rh）**：只有当当前动作正确时，用生成的摘要作为输入执行额外的k次rollout，评估未来动作的准确率，从而衡量摘要质量对后续决策的贡献。
  - 总奖励：`rt,i = rft,i + λa·rat,i + λh·rht,i`，然后通过组内归一化计算优势，优化GRPO目标函数（含KL散度正则项）。

### 2.3 算法流程（文字说明）

1. 在时间步t，智能体接收当前截图、用户指令和历史摘要。
2. 模型生成输出序列，解析为：
   - 结构化CoT（包含进度估计和决策推理）→ 用于解释
   - 动作预测（如"CLICK 'Last 30 days' at [0.68, 0.82]"）
   - 更新后的历史摘要
3. 动作执行后，环境更新，进入下一时间步。
4. 训练时先通过SFT初始化，再通过GRPO优化，RL阶段使用多组采样并计算上述三种奖励。

## 3. 实验设计

### 3.1 使用的数据集和场景

| 数据集 | 平台 | 用途 | 主要特点 |
|--------|------|------|----------|
| **Mind2Web** | Web | 离线评估跨任务/跨网站/跨域泛化 | 2350个任务，137个网站，31个领域，动作空间3种 |
| **AITW** | Android手机 | 离线评估移动端/跨域泛化 | 30K指令，715K轨迹，5个领域，动作空间11种 |
| **GUIAct** | Web + 手机 | 零样本预训练 | 多场景，统一动作空间11种 |
| **MiniWob** | Web在线 | 在线交互评估 | 动态环境，2种动作 |
| **Android World / OSWorld** | 手机/桌面 | 长时多步在线评估 | 高动态，强调历史摘要能力 |

### 3.2 评估设置

- **标准设置（Standard）**：在Mind2Web/AITW训练集上训练，在各自测试集上评估（包含分布内和跨场景泛化）。
- **零样本设置（Zero-Shot）**：在GUIAct上训练，直接测试Mind2Web/AITW（评估泛化）。
- **在线评估**：在MiniWob、Android World、OSWorld上测试成功率。

### 3.3 对比方法

- **基线方法**：MindAct、GPT-4、OmniParser、CogAgent、SeeClick、ShowUI、Qwen2-VL系列、UI-Tars等。
- **本文模型**：GUI-Rise（基于Qwen2-VL-2B / Qwen2.5-VL-3B / 7B）。

### 3.4 评价指标

- Mind2Web：元素准确率（Ele.Acc）、操作F1（Op.F1）、步骤成功率（Step SR）
- AITW：动作准确率（Action Accuracy）
- MiniWob：平均成功率（50个随机种子）

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。仅提到代码已开源（GitHub链接），但未提供详细的训练资源表。
- **可推断**：基于Qwen-VL 2B/3B/7B模型训练，通常需要至少8张A100 80GB或类似级别GPU，具体时长未报告。

## 5. 实验数量与充分性

- **实验组数**：非常充分。
  - **离线评估**：在Mind2Web（标准+零样本）和AITW（标准+零样本）上共4大组对比，每个数据集包含多个子任务/领域。
  - **在线评估**：在MiniWob（零样本+微调）、Android World、OSWorld上共4组。
  - **消融实验**：在AITW上进行了6种配置的消融（控制TST、SCoT、HS、HSR变量），验证各组件贡献。
  - **额外分析**：包含冷启动影响（图3、图4）、历史表示对比（图5）、模型规模扩展（7B实验）、案例研究（图6、图7）。
- **充分性评价**：实验设计完整，覆盖了多种泛化场景（跨任务、跨网站、跨域、零样本、在线），消融实验验证了每个核心组件的必要性，对比基线全面（包括封闭源和开源方法）。实验具有较高的客观性和公平性。不足：未报告误差棒（因计算开销大），但使用固定种子确保可重现。

## 6. 主要结论与发现

1. **跨域泛化显著提升**：在Mind2Web零样本设置下，GUI-Rise相比之前SOTA（ShowUI）在跨域split上Step SR提升38.7%；在AITW零样本设置下，整体准确率从35.9%提升至54.1%（+50.7%）。
2. **结构化推理与历史总结收益大**：消融实验表明，仅使用SFT学结构化推理会降低性能（因小模型难以独立学习），而结合RL后大幅提升；引入历史总结奖励（HSR）进一步带来增益，证明将摘要质量与后续动作挂钩的有效性。
3. **规模可扩展**：在7B模型上，GUI-Rise-7B在AITW和Mind2Web上均优于同尺度基线，显示框架可随模型规模增长受益。
4. **在线环境有效性**：在MiniWob零样本、Android World、OSWorld上均达到SOTA，证明了历史摘要设计在长时、动态任务中的优势。

## 7. 优点

- **方法创新**：将结构化CoT（进度估计+决策推理）、动作预测和历史总结三个子任务**联合集成**，形成一个完整的推理-执行-记忆循环，模仿人类导航认知过程。
- **训练策略巧妙**：两阶段训练（SFT冷启动→GRPO强化学习）避免了稀疏奖励导致的无效探索；三种奖励函数（格式、动作、历史摘要）设计精细，特别是**历史摘要奖励**通过未来动作预测来评估当前摘要质量，实现了自监督的摘要优化闭环。
- **泛化表现突出**：在多个跨域、零样本设置下大幅超越现有方法，证明了框架对未见环境和任务的鲁棒性。
- **计算效率**：相比使用全屏截图作为历史的方法，文本摘要显著降低了token开销（图5），同时提升了成功率。
- **开源与可复现**：代码已公开，实验使用固定种子。

## 8. 不足与局限

- **离线训练限制**：模型完全在离线数据上训练，无法在实时交互中适应新场景或从错误中在线学习。作者也承认此局限性，提出未来可探索在线学习方法。
- **缺少统计显著性报告**：未提供误差棒或置信区间，虽因计算成本合理，但一定程度上影响结果可靠性评估。
- **算力细节缺失**：未报告训练所需的具体GPU型号、数量和时长，不利于其他研究者复现和预估成本。
- **仅基于Qwen-VL系列**：框架虽声称兼容其他MLLM，但实验仅验证了Qwen-VL系列（2B/3B/7B），在其他模型（如LLaVA、InternVL）上的泛化性未知。
- **历史摘要生成依赖伪标签**：SFT阶段使用GPT-4o-mini生成伪标签，存在潜在的标签噪声和偏差，可能影响冷启动质量。
- **任务覆盖局限**：虽包含Web、手机、桌面，但未涉及更复杂的跨应用、多窗口场景（如Windows桌面环境）。

（完）
