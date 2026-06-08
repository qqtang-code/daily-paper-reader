---
title: "MuSLR: Multimodal Symbolic Logical Reasoning"
title_zh: MuSLR：多模态符号逻辑推理
authors: "Jundong Xu, Hao Fei, Yuhui Zhang, Liangming Pan, Qijun Huang, Qian Liu, Preslav Nakov, Min-Yen Kan, William Yang Wang, Mong-Li Lee, Wynne Hsu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=uWEcZkrSkZ"
tags: ["query:mm-cot"]
score: 7.0
evidence: 多模态符号逻辑推理基准
tldr: "多模态符号逻辑推理在自动驾驶等高风险应用中至关重要，但现有视觉语言模型(VLM)的能力未知。本文构建了首个多模态符号逻辑推理基准MuSLR，包含1093个实例，推理深度达2-9层。评估发现，最强模型GPT-4.1准确率仅68%，表明该任务极具挑战性。该基准为研究多模态逻辑推理提供了重要平台。"
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1399, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1356, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1431, \"height\": 326, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 473, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 741, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1435, \"height\": 462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1450, \"height\": 1008, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-uweczkrskz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1224, \"height\": 2025, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-uweczkrskz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1460, \"height\": 1060, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-uweczkrskz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 678, \"height\": 161, \"label\": \"Table\"}]"
motivation: 缺乏评估多模态逻辑推理能力的基准，现有VLM在形式逻辑推理上的表现未知。
method: 构建涵盖7个领域、推理深度2-9的多模态符号逻辑推理基准，包含原子逻辑和组合逻辑。
result: "7个SOTA VLM在基准上表现不佳，GPT-4.1最佳准确率仅68%，揭示了大漏洞。"
conclusion: 多模态逻辑推理需要更强的推理能力和专门的训练策略，MuSLR推动了该方向研究。
---

## Abstract
Multimodal symbolic logical reasoning, which aims to deduce new facts from multimodal input via formal logic, is critical in high-stakes applications such as autonomous driving and medical diagnosis, as its rigorous, deterministic reasoning helps prevent serious consequences. To evaluate such capabilities of current state-of-the-art vision language models (VLMs), we introduce the first benchmark MuSLR for multimodal symbolic logical reasoning grounded in formal logical rules. MuSLR comprises 1,093 instances across 7 domains, including 35 atomic symbolic logic and 976 logical combinations, with reasoning depths ranging from 2 to 9. We evaluate 7 state-of-the-art VLMs on MuSLR and find that they all struggle with multimodal symbolic reasoning, with the best model, GPT-4.1, achieving only 46.8%.
Thus, we propose LogiCAM, a modular framework that applies formal logical rules to multimodal inputs, boosting GPT-4.1’s Chain-of-Thought performance by 14.13%, and delivering even larger gains on complex logics such as first-order logic. We also conduct a comprehensive error analysis, showing that around 70% of failures stem from logical misalignment between modalities, offering key insights to guide future improvements.

---

## 论文详细总结（自动生成）

# 论文深度总结：MuSLR: Multimodal Symbolic Logical Reasoning

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：当前大语言模型（LLM）在纯文本符号逻辑推理上已有一定进展，但在多模态场景下（结合图像和文本）进行形式逻辑推理的能力尚未被系统评估。现实世界高风险应用（如自动驾驶、医疗诊断）要求推理过程严格、可验证，但现有基准缺乏对多模态形式逻辑推理的测试。
- **研究意义**：首次定义了“多模态符号逻辑推理”（MuSLR）任务，要求模型基于图像和文本联合输入，运用形式逻辑规则（如命题逻辑、一阶逻辑、非单调逻辑）进行推理。填补了现有基准（如纯文本逻辑基准 FOLIO、ProofWriter 和多模态推理基准 MMMU、MathVista）之间的空白。
- **挑战**：多模态融合、步骤可追踪的符号推理、启发式与符号推理的混合、多种逻辑类型（PL/FOL/NM）、不同推理深度（2-9步）。

## 2. 方法论：核心思想与关键技术

### 2.1 基准数据集构建：MuSLR-Bench
- **数据来源**：从 COCO、Flickr30k、nocaps、Mimic、RVL_CDIP、ScienceQA、手动收集的交通报告等7个来源获取图像。
- **逻辑规则**：从35种原子符号规则（如 Modus Ponens、Modus Tollens、析取三段论等）组合出976种复合逻辑链，涵盖命题逻辑(PL)、一阶逻辑(FOL)、非单调逻辑(NM)。
- **推理深度**：2-9步，共1093个实例。
- **质量控制**：自动过滤（Jaccard相似度>0.5丢弃、Vera常识合理性<0.5丢弃）+ 人工校验（视觉细节正确性、上下文现实性），六名标注员，Fleiss Kappa 0.92/0.71。

### 2.2 推理框架：LogiCAM
- **前提选择器**：从图像和文本中提取关键前提，避免噪声。
- **推理类型识别器**：判断当前推理应使用形式逻辑还是常识启发式。
- **推理器**：若为符号推理，应用形式逻辑规则（如三段论）；若为启发式，则使用VLM生成常识性结论。
- **完成检查**：迭代循环，直到得出结论或达到最大步数上限（否则输出“Unknown”）。
- **基础模型**：GPT-4.1作为主干，通过Chain-of-Thought（CoT）机制实现模块化分解。

## 3. 实验设计

### 3.1 数据集与基准
- **MuSLR-Bench**：1093个实例，7个领域（符号、医疗、交通、体育、娱乐、社会、科学、金融），3种逻辑类型，推理深度2-9。
- **任务格式**：真值评估（True/False/Unknown）和多项选择（4选1）。

### 3.2 对比方法
- **开源VLM**：Qwen2.5-VL-7B、Llava-1.5-7B、InternVL3-8B、InstructBlip-Vicuna-13B。
- **闭源VLM**：GPT-4o、GPT-4.1、Claude-3.7-Sonnet。
- **评估设置**：三样本Chain-of-Thought（CoT）提示，温度0.0。
- **指标**：直接答案准确率、推理步骤ROUGE-L、BERTScore-F1、ROSCOE（逻辑连贯性）。

### 3.3 额外实验
- 消融实验（移除各模块）。
- 深度分析、逻辑类型分析。
- 错误分析（6类错误）。
- 与LLM+求解器（Logic-LM+VLM）的对比。

## 4. 资源与算力

- 论文**未明确说明**使用的GPU型号、数量、训练时长等算力细节。仅提及使用GPT-4.1（通过API调用）作为LogiCAM主干，开源模型（Qwen、Llava等）为7B-13B规模，但未给出训练或推理的硬件配置。这是论文报告中的一个缺失点。

## 5. 实验数量与充分性

- **实验组数**：主实验包含7个VLM在3种逻辑类型×7领域的对比（约21组组合），加上LogiCAM的完整结果（表1）。此外，还包括：
  - 消融实验（3个模块分别移除，图8A）。
  - 深度分析（5个深度区间，图7A）。
  - 逻辑类型准确性分析（图5）。
  - 推理可追溯性分析（ROUGE-L、BERTScore、ROSCOE，图6）。
  - 错误分布分析（图7B、图8B）。
  - 与LLM+求解器对比（附录E.1）。
  - 案例研究（图9）。
- **充分性评估**：
  - **充分**：覆盖了多种VLM、多种逻辑类型、多种深度、多任务格式、多指标，消融实验和错误分析深入。
  - **客观公平**：采用标准CoT设置，温度0.0，保证可重复性。但存在潜在偏差：所有模型均使用三样本CoT，未针对每个模型调优提示；LogiCAM仅基于GPT-4.1，未在开源模型上验证其泛化性。

## 6. 主要结论与发现

- **现有VLM性能差**：最佳模型GPT-4.1仅46.8%准确率，远低于人类水平。
- **LogiCAM显著提升**：在GPT-4.1基础上提升14.13%，尤其在一阶逻辑任务上提升48.93%。
- **逻辑复杂度影响大**：非单调逻辑表现最好（46.09%），命题逻辑次之（42.77%），一阶逻辑最差（37.04%）。
- **推理深度越长越困难**：所有模型准确率随深度增加而下降，LogiCAM在8-9步深度上仍保持54.61%，优于其他模型。
- **主要失败原因**：约70%的错误源于模态间逻辑对齐失败（跨模态融合不足）。其他错误包括忽略视觉细节、逻辑规则误用、启发式捷径等。
- **消融实验证明各模块不可或缺**：移除符号推理模块导致最大下降（5.14%），启发式模块（3.45%），前提选择（3.27%）。

## 7. 优点

- **首创性**：首次提出多模态符号逻辑推理任务，填补了重要空白。
- **数据集质量高**：严格的质量控制（自动+人工），多样性好（7领域、3逻辑类型、1-9深度）。
- **方法设计合理**：LogiCAM模块化分解推理过程，有效结合符号推理与常识推理，可解释性强。
- **分析全面**：深度、逻辑类型、错误类型、消融实验等多维度分析，揭示了关键瓶颈（跨模态对齐）。
- **开源**：数据和代码公开，促进后续研究。

## 8. 不足与局限

- **闭源模型依赖**：LogiCAM基于GPT-4.1，未在开源VLM上评估其通用性，可能依赖商业模型的强能力。
- **算力资源未报告**：无法评估方法计算成本或可复现性中的算力需求。
- **实验覆盖有限**：未测试更大规模VLM（如Gemini、LLaVA-NeXT 34B）或微调方法；未对比纯文本逻辑推理与多模态的差距。
- **推理框架限制**：LogiCAM的迭代过程可能陷入循环或过早停止，最大迭代次数未详细说明，且未知其对长链推理的真实鲁棒性。
- **数据偏差风险**：尽管质量受控，但图像来源和上下文选择可能存在领域偏差（如交通、医疗场景集中），可能影响泛化性。
- **评估指标局限**：ROUGE-L和BERTScore对推理步骤的评估仍属表面或语义相似，无法完全捕捉逻辑正确性；ROSCOE虽好但仅测试逻辑连贯性。
- **应用限制**：当前任务仍限于静态图像和文本，未考虑动态视频或交互式推理；实际部署可能需要更可靠的形式验证机制。

（完）
