---
title: "MIRAGE: Assessing Hallucination in Multimodal Reasoning Chains of MLLM"
title_zh: MIRAGE：评估多模态大模型推理链中的幻觉
authors: "Bowen Dong, Minheng Ni, Zitong Huang, Guanglei Yang, Wangmeng Zuo, Lei Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=aAhhMr0TX9"
tags: ["query:mm-cot"]
score: 9.0
evidence: 分离多模态链式思考中推理幻觉的基准
tldr: 多模态大模型的幻觉来源多样，现有基准无法区分感知幻觉和推理幻觉。为此提出MIRAGE基准，通过构造问题确保图像被正确感知但推理仍出错，从而隔离推理幻觉，并提供准确率、事实性和幻觉分数等多粒度评估指标，为诊断多模态链式推理的失败提供关键工具。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1281, \"height\": 630, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1405, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 568, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 565, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1439, \"height\": 884, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1444, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1407, \"height\": 561, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1412, \"height\": 1405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 343, \"height\": 307, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 91, \"height\": 92, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 323, \"height\": 323, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 92, \"height\": 96, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 93, \"height\": 95, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 533, \"height\": 292, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 89, \"height\": 95, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 931, \"height\": 624, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 90, \"height\": 94, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 505, \"height\": 281, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 88, \"height\": 92, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 376, \"height\": 281, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 89, \"height\": 93, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 424, \"height\": 237, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1403, \"height\": 628, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aahhmr0tx9/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 424, \"height\": 238, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1369, \"height\": 437, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1422, \"height\": 969, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1309, \"height\": 219, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 613, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 706, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1242, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1239, \"height\": 212, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1290, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1197, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1445, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 593, \"height\": 175, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 505, \"height\": 166, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 674, \"height\": 146, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 633, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 533, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1457, \"height\": 1060, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 715, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1458, \"height\": 1061, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 852, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 708, \"height\": 165, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 931, \"height\": 147, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 709, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 774, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aahhmr0tx9/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 553, \"height\": 170, \"label\": \"Table\"}]"
motivation: 现有基准无法区分多模态大模型中的感知幻觉与推理幻觉。
method: 构建问题使模型正确感知图像但推理出错，并设计多粒度评估指标。
result: MIRAGE能有效揭示多模态链式推理的幻觉问题。
conclusion: 该基准为多模态链式思考的可靠性评估提供了重要支撑。
---

## Abstract
Multimodal hallucination in multimodal large language models (MLLMs) restricts the correctness of MLLMs. However, multimodal hallucinations are multi-sourced and arise from diverse causes. Existing benchmarks fail to adequately distinguish between perception-induced hallucinations and reasoning-induced hallucinations. This failure constitutes a significant issue and hinders the diagnosis of multimodal reasoning failures within MLLMs. To address this, we propose the MIRAGE benchmark, which isolates reasoning hallucinations by constructing questions where input images are correctly perceived by MLLMs yet reasoning errors persist. MIRAGE introduces multi-granular evaluation metrics: accuracy, factuality, and LLMs hallucination score for hallucination quantification. Our analysis reveals strong correlations between question types and specific hallucination patterns, particularly systematic failures of MLLMs in spatial reasoning involving complex relationships (\emph{e.g.}, complex geometric patterns across images). This highlights a critical limitation in the reasoning capabilities of current MLLMs and provides targeted insights for hallucination mitigation on specific types. To address these challenges, we propose Logos, a method that combines curriculum reinforcement fine-tuning to encourage models to generate logic-consistent reasoning chains by stepwise reducing learning difficulty, and collaborative hint inference to reduce reasoning complexity. Logos establishes a baseline on MIRAGE, and reduces the logical hallucinations in original base models. Link: \url{https://bit.ly/25mirage}.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：多模态大语言模型（MLLMs）的可靠性受限于多源幻觉，包括感知幻觉（错误理解图像内容）和推理幻觉（逻辑错误导致结论错误）。现有基准无法区分这两类幻觉，难以定位推理失败的根本原因。
- **整体含义**：本文提出 MIRAGE 基准，专门用于评估**推理幻觉**，即模型对图像感知正确但推理过程出现错误。通过构造“感知正确而推理失败”的问题，MIRAGE 能够隔离推理错误，并提供多粒度度量（准确率、事实性、LLMs 幻觉分数），为诊断与缓解 MLLMs 的推理缺陷提供关键工具。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：MIRAGE 从几何、代数、算术、科学、空间推理、逻辑、统计 7 个类别收集问题，经过难度筛选（确保开源 MLLMs 能正确描述图像但推理出错）和类别平衡采样，最终得到 1329 个问题。每个问题包含：
  - 最终答案
  - 中间推理步骤与声明
  - 完整的标准推理链
  - 图像描述与推理提示（辅助信息）
- **评估指标**：
  - **Accuracy**：最终答案正确性（解析预测答案并与标准答案匹配）
  - **Factuality**：利用 LLM 匹配预测步骤/声明与标准步骤/声明，计算 F1 分数（`F_step` 和 `F_claim`）
  - **LLMs Hallucination Score (LHS)**：通过多个 LLM 对推理链在多个维度（事实准确性、逻辑一致性、推理完整性等）打分，聚合得到不确定性估计，分数越低表示幻觉越严重
- **基线方法 Logos**：
  - **Curriculum Reinforcement Fine-Tuning (CRFT)**：基于 GRPO 算法，通过逐步增加训练数据难度（初始保留准确率>0 的样本，后续保留<0.5 的样本），并在线过滤全部奖励相同的样本，引导模型生成逻辑一致的推理链
  - **Collaborative Hint Inference (CHI)**：在推理阶段，利用辅助 LLM 识别问题类型并生成主题提示和问题特定提示，降低推理复杂度，帮助模型输出更准确的推理链
- 公式与算法流程（文字说明）：
  - GRPO 损失函数：基于采样的多个响应计算优势值 `A_i`，优化策略模型
  - CRFT 分阶段筛选数据：第一轮保留至少有一个正确响应的样本，后续轮次保留正确率低于 0.5 的样本
  - CHI：先预测问题类型，再生成 `h_topic` 和 `h_question`，以拼接方式输入模型

## 3. 实验设计：使用的数据集/场景、基准、对比方法

- **基准数据集**：MIRAGE（1329 个问题，7 个类别）
- **额外评估**：在 MathVista（标准数学推理基准）上验证 Logos 的泛化能力
- **对比方法**：
  - 黑盒 MLLMs：GPT-4o、O1、Gemini-2-Flash、Gemini-2-Flash-Thinking
  - 开源 MLLMs（~72B）：Qwen2.5-VL-72B、InternVL-2.5-78B、Qwen2-VL-72B、QvQ-72B-Preview、Virgo-72B
  - 开源 MLLMs（~7B）：Qwen2.5-VL-7B、Qwen2-VL-7B、InternVL-2.5-8B、Llama-3.2-Vision-11B、Llava-CoT-11B、R1-OneVision-7B、Mulberry-Qwen2-VL-7B 等
  - 推理增强方法：VIC（视觉推理链）、Self-Reflection、SFT 方法（如 Virgo）
- **消融实验**：逐步添加 GRPO、CRFT、`h_topic`、`h_question` 等组件，分析各自贡献
- **附加分析**：
  - 不同模型规模（3B/7B/72B）与幻觉类型的关系
  - 不同预训练数据（Qwen2-VL vs Qwen2.5-VL）的影响
  - 问题类型与幻觉类型的相关性热图
  - 手动修正推理链的实验（验证推理幻觉直接影响最终答案）

## 4. 资源与算力

- **训练资源**：Logos-7B 使用 **8 张 NVIDIA RTX A6000 GPU**，总训练时间 < 24 小时（第一阶段 16 小时，第二阶段 6 小时）；Logos-3B 更快，使用相同 GPU 配置。
- **推理资源**：使用 vLLM 框架，Logos-7B 只需单张 A6000 GPU。
- **数据标注**：自动标注成本约 22 美元，人工校验约 36 人时。
- 论文未明确说明每个模型测试的具体 GPU 数量，但推理可由单卡完成。

## 5. 实验数量与充分性

- **实验数量**：
  - 在 MIRAGE 上详细评估了 **16+ 个模型**（表 2），并按 7 个问题类型及 5 个幻觉类型分别报告。
  - 消融实验：8 组（表 8），包括不同 RL 算法、KL 散度、CRFT 阶段数、ORF 等。
  - 额外分析图：图 4（问题类型 vs 幻觉类型分布）、图 5（幻觉类型间相关性）、表 5（评估指标间相关性）等。
  - 在 MathVista 上的泛化实验（表 8 中）。
- **充分性与公平性**：
  - 实验覆盖了不同规模、不同训练阶段的模型，并进行了严格消融，验证了各组件贡献。
  - 使用 LLM-as-Judge 评估时，进行了人工交叉验证（LHS 差异率 7.5%），确保指标可靠性。
  - 对比方法包括最先进的黑盒/开源/推理增强模型，比较公平。
  - 但所有评估均在 MIRAGE 上，未在更广泛的视觉问答基准上验证，可能存在基准特定偏差。

## 6. 论文的主要结论与发现

- **模型规模、数据规模与训练阶段**显著影响逻辑幻觉、捏造幻觉和事实幻觉，但对空间幻觉改善有限，表明当前 MLLMs 的视觉推理能力薄弱，简单缩放不能提升空间推理。
- **问题类型与幻觉模式强相关**：逻辑推理问题易出现逻辑幻觉和空间幻觉；统计、科学问题常见事实幻觉；空间幻觉与其他幻觉相关性低，属于 MLLMs 特有的独立挑战。
- **现有缓解方法不足**：训练后方法（如 Self-Reflection、VIC）对基模型效果有限甚至下降；SFT 仅在较大模型上有改善，小模型面临能力瓶颈。
- **Logos 有效**：相比 Qwen2.5-VL-7B，Logos-7B 在 MIRAGE 上准确率提升 **8.3%**，事实性（F_step、F_claim）提升 8.6% 和 6.6%，逻辑幻觉减少 15.4%，同时保持 MathVista 上的优异表现（72.3%）。
- **GRPO 优于 PPO/DAPO，CRFT 优于均匀训练，ORF 提升效果**。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：
  - 首个专门隔离推理幻觉的基准（MIRAGE），通过构造“感知正确但推理失败”的任务，比现有基准更精细地诊断幻觉来源。
  - 多粒度评估指标（准确率、步骤/声明事实性、LHS），覆盖最终答案、中间结果和整体推理质量，便于追踪错误传播。
  - 引入人类-AI 协作验证标注，确保推理链质量。
- **方法论亮点**：
  - Logos 结合课程强化学习（CRFT）与协作提示推理（CHI），动态控制训练难度并降低推理复杂度，有效缓解逻辑幻觉。
  - CRFT 利用在线奖励过滤（ORF）避免无效梯度更新，训练高效。
- **实验全面性**：
  - 广泛比较了多种模型、多种训练阶段、多种幻觉类型。
  - 进行了相关性分析（问题类型-幻觉、幻觉间、指标间），提供了深入洞察。
  - 手动修正推理链的实验直接验证了推理幻觉对答案的影响，强化了方法动机。

## 8. 不足与局限

- **实验覆盖**：MIRAGE 仅包含单图像问题，未覆盖多图像或视频场景，限制了时间/跨图像幻觉的评估。论文提及可通过拼接图像转换，但未直接验证。
- **缓解能力有限**：Logos 对空间幻觉和事实幻觉的改善不显著，因为 RL 未引入新知识，且基模型空间推理能力先天不足。
- **数据偏差**：问题来源可能偏向数学/逻辑类，场景多样性有限；自动标注和 LLM 判分可能存在自身偏差，尽管有人工校验，但校验规模有限（100 样本）。
- **理论分析欠缺**：论文未深入解释 MLLMs 产生推理幻觉的根因，仅通过相关性分析给出观察。
- **泛化性**：Logos 在 MIRAGE 和 MathVista 上表现好，但未在更多视觉推理基准（如 VQAv2、GQA）上验证，可能过拟合到数学推理。
- **计算资源消耗**：虽然总训练时间<24 小时，但 8×A6000 GPU 的成本仍较高，对小型研究团队可能不友好。

（完）
