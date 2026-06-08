---
title: "LogicTree: Improving Complex Reasoning of LLMs via Instantiated Multi-step Synthetic Logical Data"
title_zh: 逻辑树：通过实例化多步合成逻辑数据改进大语言模型的复杂推理
authors: "Zehao Wang, Lin Yang, Jie Wang, Kehan Wang, Hanzhu Chen, Bin Wang, Jianye HAO, Defu Lian, Bin Li, Enhong Chen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=z4AMrCOetn"
tags: ["query:mm-cot"]
score: 8.0
evidence: 合成多步逻辑推理数据以支持复杂任务
tldr: 针对大语言模型在复杂多步推理上的不足，提出LogicTree框架，通过迭代搜索合成高质量、高复杂度的逻辑推理数据集，有效提升了模型在需要多步推理的任务上的表现，为长链推理研究提供了数据支撑。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 829, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 867, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1437, \"height\": 814, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1140, \"height\": 787, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1374, \"height\": 143, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1403, \"height\": 880, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1366, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1169, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1319, \"height\": 654, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z4amrcoetn/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1369, \"height\": 734, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1445, \"height\": 1637, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1376, \"height\": 353, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1303, \"height\": 660, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1450, \"height\": 1543, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1351, \"height\": 393, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1382, \"height\": 334, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 493, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1157, \"height\": 948, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1460, \"height\": 804, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1320, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1451, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z4amrcoetn/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1455, \"height\": 1555, \"label\": \"Table\"}]"
motivation: 现有逻辑推理数据生成方法依赖于预定义模板，缺乏对真实场景的适应性。
method: 提出LogicTree框架，通过迭代搜索适用的逻辑规则来动态合成多步推理数据。
result: 生成的数据集显著提升了LLM在复杂逻辑推理基准上的准确率。
conclusion: LogicTree为提升LLM长链推理能力提供了有效的数据增强途径。
---

## Abstract
Despite their remarkable performance on various tasks, Large Language Models (LLMs) still struggle with logical reasoning, particularly in complex and multi-step reasoning processes. 
Among various efforts to enhance LLMs' reasoning capabilities, synthesizing large-scale, high-quality logical reasoning datasets has emerged as a promising direction. 
However, existing methods often rely on predefined templates for logical reasoning data generation, limiting their adaptability to real-world scenarios. 
To address the limitation, we propose **LogicTree**, a novel framework for efficiently synthesizing multi-step logical reasoning dataset that excels in both complexity and instantiation.
By iteratively searching for applicable logic rules based on structural pattern matching to perform backward deduction, **LogicTree** constructs multi-step logic trees that capture complex reasoning patterns. 
Furthermore, we employ a two-stage LLM-based approach to instantiate various real-world scenarios for each logic tree, generating consistent real-world reasoning processes that carry contextual significance.   This helps LLMs develop generalizable logical reasoning abilities across diverse scenarios rather than merely memorizing templates.
Experiments on multiple benchmarks demonstrate that our approach achieves an average improvement of 9.4\% in accuracy on complex logical reasoning tasks.

---

## 论文详细总结（自动生成）

# 论文《LogicTree: Improving Complex Reasoning of LLMs via Instantiated Multi-step Synthetic Logical Data》中文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：尽管大语言模型（LLM）在许多任务上表现出色，但在复杂、多步的逻辑推理方面仍存在显著不足。高质量的逻辑推理数据是提升该能力的关键，但现有合成数据方法存在两个主要局限：
  - 复杂性不足：通常只生成简单的推理模式，规则类型有限、推理步骤浅。
  - 场景实例化不足：使用模板将符号与随机实体组合，缺乏上下文相关性和真实世界语义，导致模型学到的推理能力难以泛化。
- **整体含义**：逻辑推理是编码、数学等高级认知能力的基础。构建兼具复杂性和真实场景实例化能力的高质量数据集，对提升LLM的泛化推理能力至关重要。

## 2. 方法论

### 2.1 核心思想
- **LogicTree** 是一个新颖的框架，通过第一阶逻辑规则（FOL）生成复杂的多步逻辑推理树，然后利用LLM将树中的符号表达式实例化为带有真实场景的自然语言推理过程。最终生成包含前提、结论-答案对及推理过程的数据实例。

### 2.2 关键技术细节

- **逻辑推理树生成**：
  - 采用**向后演绎**（backward deduction）方法：从根节点（一个随机生成的公式）开始，基于**结构模式匹配**（structural pattern matching）搜索适用的逻辑规则，将叶子节点不断分解为子节点。
  - 结构模式匹配：比较公式的抽象语法树（AST）的运算符骨架是否同构，而不要求完全一致。例如，`(A ∨ B) → (¬C)` 与 `F → G` 匹配，可使用假言三段论规则。
  - 生成树包含命题逻辑和FOL规则（如Modus Ponens、Syllogism、Universal Instantiation等），规则总数达190种，深度可控制在2~15步。

- **推理场景实例化（两阶段LLM方法）**：
  - **阶段一（逻辑树实例化）**：将叶子节点中的原子公式输入LLM，要求其赋予真实世界语句，并保持逻辑关系一致。通过控制主题域（如公共卫生、经济等）确保多样性。
  - **阶段二（推理过程翻译）**：按深度降序排列中间节点，LLM将符号推理步骤逐条翻译为自然语言推理过程，以正确符号骨架引导，避免推理错误。
  - 最终通过后处理验证逻辑一致性，过滤掉约8.73%的错误实例。

- **数据构造**：使用叶子节点语句作为前提，根节点为“True”结论，根节点否定为“False”结论，引入无关语句作为“Uncertain”结论。

## 3. 实验设计

### 3.1 数据集与Benchmark
- **训练数据**：生成5,000个逻辑树（深度2~15），每个树实例化为3个不同场景，共15,000个问题，过滤后约13.8k高质量实例。
- **评估Benchmark**：
  - LogicBench：单一步骤推理规则评估。
  - LogiQA2.0：真实公务员考试逻辑题。
  - FOLIO：一阶逻辑专家标注数据集。
  - BBH-Logic（三个任务：causal judgment, formal fallacies, logical deduction）。
  - AGIEval（LSAT子任务：LR和AR）。
  - Multi-LogiEval：按推理步骤（1~5）分类评估多步推理能力。
- 额外泛化实验：Proofwriter（逻辑）、Mathqa（数学）、GPQA（科学）、Humaneval（代码）、Commonsenseqa（常识）、MNLI（自然语言推理）。

### 3.2 对比方法
- Vanilla（原始模型）
- PARARULE：模板化多步演绎。
- LogicAsker：原子规则评估与样本生成。
- FLD×2：系统性设计的多步推理数据合成。

### 3.3 模型与训练设置
- 模型：Llama-3.1-8B/70B, Qwen2.5-7B/1.5B/3B, Mistral-7B-v0.3, DeepSeek-R1-Distill系列。
- 微调策略：小模型（<8B）全微调，70B使用LoRA。
- 超参数：学习率1e-6（8B）/3e-6（1.5B/3B）/2e-5（70B LoRA），序列长度4096，全局batch 128，训练3 epoch。使用DeepSpeed、梯度检查点、BF16。
- 学习率调度：余弦，warmup 0.03。

## 4. 资源与算力
- 论文**未明确说明**使用的GPU型号、数量及总训练时长。
- 仅提及使用DeepSpeed进行高效内存管理、BF16精度。训练3 epoch的数据量约13.8k样本，对小模型（7B-8B）全微调、大模型（70B）LoRA，计算资源需求中等，但具体硬件细节缺失。

## 5. 实验数量与充分性

- **实验数量充足**：覆盖6个主逻辑推理benchmark（LogicBench, LogiQA2.0, FOLIO, BBH-Logic, AGIEval-LR/AR），以及Multi-LogiEval按深度分组的5个难度级别。
- **消融实验**：3组关键消融（无场景实例化、无推理过程实例化、不同多样性数量（num=1~5）），验证各组件贡献。
- **泛化实验**：6个额外任务（逻辑、数学、代码、NLI等），检验跨域能力。
- **多模型验证**：包含4个模型家族、7种参数量（1.5B~70B），包括推理增强模型（DeepSeek-R1-Distill）。
- **公平性**：与3种主流合成数据方法在相同设置下对比，报告均值与标准差（重复实验）。结论客观。
- 总体**充分且客观**，但缺乏在不同随机种子下的更多重复（仅报告标准误，未标明重复次数）。

## 6. 主要结论与发现

1. **LogicTree显著提升复杂逻辑推理性能**：在Llama-3.1-8B上平均提升9.4%（相对20%），在Qwen2.5-7B上提升4.5%，在Mistral-7B上提升3.1%，在Llama-3.1-70B上提升2.9%。几乎所有benchmark均超越所有基线方法。
2. **在深度推理任务上优势更明显**：Multi-LogiEval中，LogicTree在d3~d5深度上准确率显著高于基线，其他方法随深度增加急剧下降。
3. **泛化能力增强**：除逻辑任务外，在数学（Mathqa +5.2%）、代码（Humaneval +6.2%）、NLI（MNLI +8.7%）等任务上也有提升，表明学习到一般推理能力而非记忆。
4. **消融验证关键组件**：
   - 实例化场景比纯符号训练提升更大（+10.6 vs +6.3）。
   - 自然语言推理过程进一步增益（+88.3 vs +90.6）。
   - 多样场景（num=3~4）最优；num=1导致过拟合。
5. **数据质量高**：GPT-4o评估逻辑一致性达97.6%，LLM评估真实性与上下文丰富性均优于基线。

## 7. 优点

- **方法创新**：提出基于结构模式匹配的向后演绎生成复杂逻辑树，突破模板限制；两阶段LLM实例化策略巧妙规避LLM自身推理错误。
- **数据质量与多样性**：190种逻辑规则、深度可控、场景覆盖50+主题，实现高复杂性与高实例化。
- **系统性验证**：在多种模型、多种任务上全面评估，消融实验设计合理，结论可靠。
- **实际可用性**：开源细节待定，但方法论可复现；自动过滤机制确保数据质量。
- **与长链推理相关**：为CoT等需要多步推理的场景提供了高质量训练数据。

## 8. 不足与局限

- **算力信息缺失**：未报告GPU型号、数量、总训练时长，影响可复现性评估。
- **实验重复次数未明确**：虽报告标准误，但未说明是几次独立实验（可能是随机抽样标准误）。需更明确统计显著性。
- **数据规模较小**：仅13.8k实例，可能不足以支撑更大规模模型（如70B以上）的充分微调。
- **特定领域覆盖有限**：泛化实验中常识、科学任务提升微弱，表明LogicTree主要强化推理而非知识；知识密集型任务需额外处理。
- **无法与其他推理范式集成**：仅聚焦形式逻辑，未融合常识推理、时间推理等，综合推理能力受限。
- **LLM依赖**：实例化依赖GPT-4等较强LLM，可能引入隐蔽偏差；即使过滤，仍存在模式化倾向。
- **应用限制**：合成数据基于形式逻辑，与现实世界复杂、非形式化推理仍有差距；模型在开放域推理中可能缺乏鲁棒性。

（完）
