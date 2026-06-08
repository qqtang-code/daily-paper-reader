---
title: "Can MLLMs Reason in Multimodality? EMMA: An Enhanced MultiModal ReAsoning Benchmark"
title_zh: MLLMs能否进行多模态推理？EMMA：增强的多模态推理基准
authors: "Yunzhuo Hao, Jiawei Gu, Huichen Will Wang, Linjie Li, Zhengyuan Yang, Lijuan Wang, Yu Cheng"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=v26vwjxOEz"
tags: ["query:mm-cot"]
score: 9.0
evidence: 多模态推理基准测试
tldr: 多模态大模型在有机多模态推理上的能力仍未被充分探索。本文提出EMMA基准，涵盖数学、物理、化学和编程，要求跨模态融合推理，而非独立处理各模态。评估表明当前MLLMs在该基准上表现不足，揭示了多模态推理的挑战。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有基准偏向文本主导或依赖浅层视觉线索，无法充分评估融合视觉和文本的推理。
method: 构建EMMA基准，包含需要跨模态推理的数学、物理、化学和编程任务。
result: 评估显示当前多模态大模型在该基准上表现不足。
conclusion: EMMA为多模态推理能力提供了更具挑战性的测试平台。
---

## Abstract
The ability to organically reason over and with both text and images is a pillar of human intelligence, yet the ability of Multimodal Large Language Models (MLLMs) to perform such multimodal reasoning remains under-explored. Existing benchmarks often emphasize text-dominant reasoning or rely on shallow visual cues, failing to adequately assess integrated visual and textual reasoning. We introduce EMMA (Enhanced MultiModal reAsoning), a benchmark targeting organic multimodal reasoning across mathematics, physics, chemistry, and coding. EMMA tasks demand advanced cross-modal reasoning that cannot be addressed by reasoning independently in each modality, offering an enhanced test suite for MLLMs' reasoning capabilities. Our evaluation of state-of-the-art MLLMs on EMMA reveals significant limitations in handling complex multimodal and multi-step reasoning tasks, even with advanced techniques like Chain-of-Thought prompting and test-time compute scaling underperforming. These findings underscore the need for improved multimodal architectures and training paradigms to close the gap between human and model reasoning in multimodality.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

现有大多数多模态基准主要评估文本主导的推理或浅层视觉理解，例如许多数学问题可以通过图像中的文本描述直接解决，或只需一次视觉感知即可回答，未能真正考验模型在**文本与视觉之间有机融合推理**的能力。人类解决复杂问题时常需要反复在语言和视觉之间切换（如模拟力的分解、折叠纸张等）。为此，论文提出 **EMMA（Enhanced MultiModal ReAsoning）** 基准，专门针对“有机多模态推理”需求，涵盖数学、物理、化学和编程四个领域，要求模型不能独立处理各模态，而必须进行跨模态交织推理。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：构建一个**仅通过文本推理或单次视觉处理无法解决**的测试集，确保每个问题都强制要求模型进行深度的多模态互动推理（如空间想象、多步视觉模拟、化学电子流向推理）。
- **数据构建流程（两步法）**：
  1. **严格过滤**：从现有基准（MathVista、Math-Vision、OlympiadBench、MMMU、EXAMS-V等）中筛选问题。首先仅用文本部分通过LLM（Llama-3-70B、GPT-4o、Qwen2-72B）测试，丢弃可仅靠文本回答的问题；进一步用GPT-4o生成图像标题，再将“文本+标题”输入模型，若任意模型在10次中正确≥5次则丢弃，确保问题不能仅靠单次视觉+语言描述解决。
  2. **手动扩充**：对每个学科，由领域专家或GPT-4o辅助（经专家验证）对剩余问题按所需推理技能进行细粒度分类，然后针对各技能类别**手动收集或构造新问题**。特别是化学部分（利用SMiCRM和RDKit生成大量新题）和编程部分（从头构造可视化代码选择题），以及从RAVEN、Learn AP Physics、Khan Academy等来源补充。
- **数据规模**：共2,788个问题，其中1,796个为新构造；72%为选择题，28%为开放式；93%的问题包含图像，7%的选项包含图像；10%的问题含多张图。
- **分类标签**：每个问题标有细粒度技能类别，例如数学包括2D变换、3D空间模拟、路径追踪、多跳物体计数、图案推理等；物理包括3D场模拟、图推理、视觉分解模拟等；化学包括键计数、结构识别、反应模拟等；编程包括图表编码选择、代码生成图表选择、修改代码等。

### 3. 实验设计

- **数据集**：完整EMMA（2,788题）与平衡子集EMMA-mini（400题，每学科100题）。
- **基准对比**：人类专家（每学科两位专家，取平均）在EMMA-mini上得分为77.75%。
- **评估模型**（10个SOTA MLLM）：
  - 闭源：GPT-4o、Claude 3.5 Sonnet、Gemini 2.0 Flash、Gemini 2.0 Flash Thinking（两个版本）、o1。
  - 开源：Qwen2-VL-72B-Instruct、LLaVA-Onevision-72B、InternVL2-Llama3-76B、InternVL2.5-78B、QVQ-72B-Preview。
- **提示策略**：直接提示 vs. Chain-of-Thought (CoT) 提示；对o1、QVQ和Gemini Flash Thinking使用其自带的链式推理模式。
- **测试时间缩放**：对GPT-4o、Gemini 2.0 Flash、Gemini 2.0 Flash Thinking在EMMA-mini上采用多数投票、Best-of-N（自奖励模型或Gemini Flash Thinking奖励模型）、锦标赛选择，N=1,2,4,8,16。
- **额外消融**：在数学部分使用专门数学奖励模型Qwen2.5-Math-RM-72B进行Best-of-N（但需图像标题输入）。
- **评估指标**：准确率（Accuracy）。

### 4. 资源与算力

论文中**未明确说明**所使用的GPU型号、数量和训练时长等算力信息。仅提及在数据过滤和模型推理时使用了vLLM和Transformers库加载模型，推断评估是在推理阶段完成，未涉及模型微调或训练。因此无法提供具体算力统计。

### 5. 实验数量与充分性

- **主要对比实验**：10个模型在完整EMMA（2,788题）和EMMA-mini（400题）上的两种提示策略结果，共约20组主要结果（部分模型仅测mini）。
- **CoT消融**：每个模型比较直接提示与CoT提示，生成对比表格（表2）。
- **测试时间缩放实验**：3个基础模型×3种方法×5个N值，共45组（部分组合因上下文限制未全部执行），并与人类专家、随机基线对比。
- **误差分析**：对o1在数学和编程部分错误进行四类分类（感知错误、视觉推理错误、文本推理错误、知识缺失），并配以多个案例分析。此外分析CoT对不同技能类别的影响。
- **充分性评价**：实验设计较为全面，覆盖了多模态推理的多个维度（不同学科、提示策略、测试时扩展、错误类型）。但物理问题数量较少（仅156题），可能影响统计稳定性。部分模型（o1、QVQ）因速率限制仅在mini上评估，未在全集上报告。此外未探索视觉CoT或多模态链式思维，实验局限性在文中提及。

### 6. 论文的主要结论与发现

1. **MLLMs多模态推理能力严重不足**：在EMMA-mini上，最好模型Gemini 2.0 Flash Thinking-0121仅48.00%，低于人类专家29.75%。所有模型在所有学科上均表现欠佳。
2. **文本CoT效果不一致**：对闭源模型一般有帮助（最高提升3%），但对开源模型（如Qwen2-VL、InternVL2.5）反而损害性能（降低超过6%）。认为视觉密集型任务（如2D变换）不适合文本CoT，而语言辅助的任务（如多跳计数）有效。
3. **测试时间缩放提升有限**：即使N=16，多数投票或基于更强奖励模型的Best-of-N也只能带来小幅度提升（最高7.5%），仍远不如人类。主要瓶颈在于模型本身无法产生正确的视觉推理步骤。
4. **视觉推理是主要瓶颈**：错误分析显示52.83%的错误来自视觉推理失败（如空间模拟、场方向判断等），而感知错误仅占30.19%。强模型（如o1）在需要精细多步视觉模拟的任务上经常出错。
5. **不同学科难度差异**：物理相对表现较好（与人类差距最小），化学、数学和编程差距大（>30%）。化学知识型计数（键数）最为困难，模型几乎随机。

### 7. 优点

- **更严格的过滤机制**：不仅去除可仅用文本回答的问题，还进一步去除“文本+图像标题”可解答的问题，确保剩余问题必须进行深度视觉推理。这比MMMU-Pro的过滤更严格。
- **手动构造大量高质量新题**：尤其在化学（1,156个新问题）和编程（564个新题）领域填补了现有基准空白，编程题首次采用选择题形式评估可视化代码理解，避免使用不可靠的MLLM裁判。
- **细粒度技能标注**：每个问题都标注了所需的具体推理技能（如2D变换、3D场模拟、反应模拟等），便于分析模型在特定能力上的弱点。
- **多维度实验**：综合评估了提示策略、测试时间缩放、不同奖励模型，并进行了详细的错误分类和案例分析。

### 8. 不足与局限

- **物理部分数据量偏少**：仅156题，且大部分从现有基准过滤后仅剩80题，可能不足以代表物理多模态推理的全貌。
- **手动筛选和构造可能存在偏差**：人工参与可能引入无意识的偏好，例如化学题过度聚焦于有机化学和电子推送图，覆盖范围有限。
- **未探索视觉CoT或多模态思维链**：论文仅测试了文本CoT，未考虑模型内部生成视觉推理图或使用外部视觉工具（如作图辅助）的情况。这可能低估了未来模型的潜力。
- **开源模型CoT性能下降的原因未深入解释**：论文提出猜想但缺乏实验验证（如分析推理路径正确率、可视化注意力等），结论较初步。
- **仅采用问答格式**：未评估生成式任务（如多步对话、交互式推理），实用性受限。
- **基准规模相对较小**：总问题数2,788，在细分类别下每个子类样本数较少（如物理路径追踪仅13题），可能影响统计显著性。
- **未提供训练阶段算力信息**：无法评估构建和评估的成本，对复现和公平性分析略有影响。

（完）
