---
title: "Visual Thoughts: A Unified Perspective of Understanding Multimodal Chain-of-Thought"
title_zh: 视觉思维：理解多模态链式推理的统一视角
authors: "Zihui Cheng, Qiguang Chen, Xiao Xu, Jiaqi WANG, Weiyun Wang, Hao Fei, Yidong Wang, Alex Jinpeng Wang, Zhi Chen, Wanxiang Che, Libo Qin"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=xPcKmKSEis"
tags: ["query:mm-cot"]
score: 9.0
evidence: 多模态CoT的统一视角及视觉思维概念
tldr: "多模态链式推理(MCoT)提升了大视觉语言模型的性能，但其机制尚不明确。本文首次揭示MCoT通过融入'视觉思维'（即传达图像信息的中间表示）来增强推理，且效果与格式无关，只取决于表达的清晰简洁。该统一视角解释了文本型MCoT和交错型MCoT的共性，并为设计更有效的MCoT方法提供了指导。"
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-xpckmkseis/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1408, \"height\": 565, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xpckmkseis/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1431, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xpckmkseis/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1414, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xpckmkseis/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1436, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xpckmkseis/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 582, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xpckmkseis/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1396, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xpckmkseis/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 658, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xpckmkseis/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1148, \"height\": 745, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xpckmkseis/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1303, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xpckmkseis/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1298, \"height\": 839, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xpckmkseis/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 558, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xpckmkseis/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1436, \"height\": 358, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-xpckmkseis/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1433, \"height\": 746, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xpckmkseis/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 572, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xpckmkseis/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1431, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xpckmkseis/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1432, \"height\": 235, \"label\": \"Table\"}]"
motivation: 多模态CoT的改善机制尚不明确，缺乏统一理论解释。
method: "通过分析现有MCoT方法，提出'视觉思维'概念，并设计实验验证其在不同格式下的作用。"
result: 实验表明，MCoT的有效性源于视觉思维的清晰度，而非格式选择，且与模型规模正相关。
conclusion: 视觉思维是理解多模态CoT的关键，未来应聚焦于生成更精确的视觉思维。
---

## Abstract
Large Vision-Language Models (LVLMs) have achieved significant success in multimodal tasks, with multimodal chain-of-thought (MCoT) further enhancing performance and interpretability. Recent MCoT methods fall into two categories: (i) Textual-MCoT (T-MCoT), which takes multimodal input and produces textual output; and (ii) Interleaved-MCoT (I-MCoT), which generates interleaved image-text outputs. Despite advances in both approaches, the mechanisms driving these improvements are not fully understood.  To fill this gap, we first reveal that MCoT boosts LVLMs by incorporating $\textit{visual thoughts}$, which convey image information to the reasoning process regardless of the MCoT format, depending only on clarity and conciseness of expression. Furthermore, to explore visual thoughts systematically, we define four distinct forms of visual thought expressions and analyze them comprehensively. Our findings demonstrate that these forms differ in clarity and conciseness, yielding varying levels of MCoT improvement. Additionally, we explore the internal nature of visual thoughts, finding that visual thoughts serve as intermediaries between the input image and reasoning to deeper transformer layers,  enabling more advanced visual information transmission. We hope that the visual thoughts can inspire further breakthroughs for future MCoT research.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：多模态链式推理（MCoT）能显著提升大视觉语言模型（LVLM）的性能，但其背后的机制尚不明确。现有的两类MCoT方法（文本型T-MCoT和交错型I-MCoT）有不同的表现形式和效果，但缺少一个统一的理论框架来解释它们究竟如何提升推理能力。
- **动机**：无论是文本形式的推理思路还是图文交错的推理路径，其成功的根源究竟是什么？是否有一个共同的本质？作者试图通过“视觉思维”（Visual Thought）这一概念来填补这一空白。
- **整体含义**：论文提出，MCoT的改进本质上来源于在推理过程中融入了“视觉思维”——一种中间跨模态表示，它从原始图像中提取与任务相关的视觉信息并以高效的方式缓存下来，供后续推理步骤使用。视觉思维的核心在于表达的**清晰性**和**简洁性**，而非其具体格式（文本或图像）。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：将“视觉思维”定义为一种中间推理步骤（Re<sub>VT</sub>），它从视觉输入VI和先前步骤R<sub>&lt;i</sub>中提取信息，由任务问题Q<sub>T</sub>和指令IE<sub>VT</sub>驱动，生成下一步推理R<sub>i</sub>。
- **关键技术细节**：
    - 视觉思维作为“视觉缓存”（visual cache），减少了对原始图像的重复处理，使模型可以进行更深层的多步推理。
    - 将视觉思维归纳为四种表达形式（两类MCoT下的四种策略）：
        1. **自然语言（N-LANG）**：如生成图像描述。
        2. **结构化语言（S-LANG）**：如生成场景图（JSON格式）。
        3. **编辑图像（E-IMG）**：使用外部工具（如Grounding DINO、SAM）对原图进行标注、分割等。
        4. **生成图像（G-IMG）**：使用扩散模型（如DALL-E 3）生成与推理逻辑相关的新图像。
- **公式（文字说明）**：
    - 视觉思维生成概率：当概率π≥π阈值时，生成视觉思维；否则生成衍生推理步骤。
    - 文本MCoT（T-MCoT）中的视觉思维生成使用文本token概率π<sub>text</sub>。
    - 图像MCoT（I-MCoT）中的视觉思维生成使用图像token概率π<sub>image</sub>。
- **算法流程**：两阶段推理：第一阶段生成视觉思维（根据提示指令）；第二阶段将视觉思维作为额外上下文，结合原问题生成最终推理路径和答案。

### 3. 实验设计：数据集、场景、基准方法与对比方法
- **数据集与场景**：
    - **MMVP**：评估粗粒度感知（如识别显眼物体）。
    - **V*Bench**：评估位置（position）和属性（attributes）等细粒度感知。
    - **M3CoT**：涵盖物理、社会、时间等多轮推理场景。
    - **CoMT**：评估视觉删除、选择、更新等复杂推理操作。
    - **IsoBench**（附录B）：数学、图形等纯文本空间想象任务。
- **基准方法（baselines）**：
    - **w/o VT**：无视觉思维，直接推理。
    - **N-LANG**：自然语言视觉思维。
    - **S-LANG**：结构化语言视觉思维。
    - **E-IMG**：编辑图像视觉思维。
    - **G-IMG**：生成图像视觉思维。
    - **Caption-Only**：仅用图像标题（对比视觉思维）。
    - **Query-Only**：仅用问题（无图像）。
    - **Direct**：直接回答（不进行CoT）。
- **对比模型**：LLaVA-1.5-7B、Qwen2-VL-7B、GPT-4o-mini、GPT-4o。

### 4. 资源与算力
- 文中在附录A中提到：所有开源模型（LLaVA-1.5、Qwen2-VL）在2张A6000 48G GPU上完成推理。
- GPT-4o和GPT-4o-mini通过API调用。
- 未明确说明训练时长，属于推理分析任务，不涉及模型训练。

### 5. 实验数量与充分性
- **实验数量**：
    - 主实验（表1）：4个模型 × 4种视觉思维 × 4个数据集（含子任务） = 大量对比。
    - 有效性验证（图4、图12）：含图像形式、文本形式、无视觉思维、仅标题等对比。
    - 相关性分析（图6）：人工评估100个样本的表达清晰度、简洁性，计算与准确率的相关系数。
    - 噪声分析（图7）：调节编辑/生成图像的噪声水平。
    - 内部机制分析（图8-10）：注意力分布、信息流阻断、显著性分析。
    - 额外消融（表3）：w/o CoT对比。
    - 未来工作（表4）：集成多种视觉思维（Diverse-VT）。
- **充分性与客观性**：
    - 实验覆盖了不同复杂度（简单、中等、困难）、不同模态（文本、图像）、不同模型系列（开源、商业）。
    - 采用多次重复（如Maj@4）确保稳定性。
    - 人工评估有明确评分标准和多名标注员。
    - 控制变量（如w/o VT的构造方式说明，防止上下文扰动）。
    - 总体实验设计比较全面、公平。

### 6. 论文的主要结论与发现
- **核心结论**：MCoT的提升统一来源于“视觉思维”，其有效性取决于表达的清晰性和简洁性，而非具体格式（文本或图像）。
- **具体发现**：
    1. 移除视觉思维会导致性能下降，甚至低于仅从查询推理。
    2. 图像形式的视觉思维在复杂场景下优于文本形式。
    3. 视觉思维不是图像的忠实再现，而是经过凝练的视觉逻辑缓存。
    4. 不同表达形式适用于不同场景：N-LANG适合粗粒度感知；S-LANG适合关系推理；E-IMG适合细粒度分析；G-IMG适合多步迭代推理。
    5. 视觉思维能够将视觉信息传递到更深的Transformer层（超过12层），这是原始图像无法做到的。
    6. 模型架构（层数）对视觉思维传递的影响大于参数规模。

### 7. 优点：方法或实验设计上的亮点
- **理论创新**：首次提出统一视角“视觉思维”，连接了T-MCoT和I-MCoT，为后续研究提供理论基础。
- **系统分类**：清晰界定四种表达形式，并针对每种形式设计标准化的两阶段提示流程。
- **深入机制分析**：不仅验证有效性，还通过注意力分析、信息流分析揭示了内部工作原理（如注意力转移、深度传递）。
- **控制严谨**：在有效性验证中，通过替换视觉思维的占位符和文本描述来排除上下文干扰（附录B.3）。
- **人工评估**：对清晰度、简洁性进行人工打分，并提供详细的评分标准，增加了结果的可靠性。

### 8. 不足与局限
- **实验覆盖**：
    - 排除了多轮视觉思维交互的场景（如连续生成多个图像）。
    - I-MCoT中G-IMG依赖于外部工具DALL-E 3，可能引入生成噪声（图7已分析）。
    - 主要评估了LVLM的推理能力，未充分涉及训练或微调场景。
- **偏差风险**：
    - 人工评估样本量（100个）相对较小，可能统计代表性有限。
    - 仅使用GPT-4o作为标题生成器，可能存在模型特定偏差。
- **应用限制**：
    - I-MCoT的推理成本（时间、费用）远高于T-MCoT（表2），不利于实际部署。
    - 外部工具（如Grounding DINO、Stable Diffusion）的质量直接影响视觉思维效果。
    - 由于缺乏真正的Any-to-Any LVLM，G-IMG采用外部模型生成，并非模型自身推理。

（完）
