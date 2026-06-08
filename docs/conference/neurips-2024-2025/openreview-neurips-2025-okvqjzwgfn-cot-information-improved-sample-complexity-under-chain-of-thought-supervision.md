---
title: "CoT Information: Improved Sample Complexity under Chain-of-Thought Supervision"
title_zh: CoT信息：链式思维监督下的样本复杂度改进
authors: "Awni Altabaa, Omar Montasser, John Lafferty"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=OkVQJZWGfn"
tags: ["query:mm-cot"]
score: 7.0
evidence: 链式思维监督的统计理论，证明其降低样本复杂度
tldr: 从统计学习理论出发，本文形式化定义了CoT信息，衡量链式思维对区分不同假设的额外判别力。理论证明，与标准输入输出学习相比，CoT监督能显著降低样本复杂度，加速多步推理函数的学习。该工作为理解CoT的有效性提供了理论基础。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-okvqjzwgfn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1366, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-okvqjzwgfn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1328, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-okvqjzwgfn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 505, \"height\": 503, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-okvqjzwgfn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 1629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-okvqjzwgfn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 654, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-okvqjzwgfn/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 642, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-okvqjzwgfn/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 648, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-okvqjzwgfn/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 656, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-okvqjzwgfn/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 653, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-okvqjzwgfn/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 656, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-okvqjzwgfn/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1043, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-okvqjzwgfn/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 688, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-okvqjzwgfn/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 689, \"height\": 457, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-okvqjzwgfn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1077, \"height\": 406, \"label\": \"Table\"}]"
motivation: 标准监督学习在多步复杂函数学习中需要大量样本，缺乏对中间推理步骤的利用。
method: 定义CoT信息量，从统计学习角度分析链式思维监督如何提供额外判别力，并推导其样本复杂度上界。
result: 理论证明CoT监督可达到更快的学习速率，与实验结果一致，验证了中间步骤的重要性。
conclusion: CoT监督从根本上改善了多步推理任务的学习效率，为设计更优的提示策略提供了理论指导。
---

## Abstract
Learning complex functions that involve multi-step reasoning poses a significant challenge for standard supervised learning from input-output examples. Chain-of-thought (CoT) supervision, which augments training data with intermediate reasoning steps to provide a richer learning signal, has driven recent advances in large language model reasoning. This paper develops a statistical theory of learning under CoT supervision. Central to the theory is the *CoT information*, which measures the additional discriminative power offered by the chain-of-thought for distinguishing hypotheses with different end-to-end behaviors. The main theoretical results demonstrate how CoT supervision can yield significantly faster learning rates compared to standard end-to-end supervision, with both upper bounds and information-theoretic lower bounds characterized by the CoT information.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：标准监督学习（输入-输出对）在学习多步推理的复杂函数时，需要大量样本，且难以捕捉中间推理过程。链式思维（CoT）监督通过提供中间推理步骤（例如自然语言描述的执行轨迹）来丰富学习信号，已被广泛用于大型语言模型的推理增强。然而，CoT监督为何能带来统计效率提升，缺乏严格的理论解释。
- **整体含义**：本文从统计学习理论出发，引入**CoT信息量（CoT information）** 这一核心概念，量化链式思维对区分具有不同端到端行为的假设的额外判别力。理论证明，CoT监督可以显著降低样本复杂度，并给出信息论意义的上下界，从而为CoT的有效性提供理论基础。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将CoT监督建模为假设类 \(H \subset (\mathcal{Y} \times \mathcal{Z})^{\mathcal{X}}\)，每个假设 \(h\) 同时输出最终答案 \(y\) 和中间步骤 \(z\)。训练时基于 \((x, y, z)\) 的联合样本，测试时仅评估端到端误差 \(R_{\text{e2e}}(h) = P[h_{\text{e2e}}(x) \neq h_{\star}^{\text{e2e}}(x)]\)。关键挑战在于训练目标（CoT风险）和测试指标（端到端风险）的不对称性。
- **关键技术细节**：
  - **CoT信息量定义**：
    \[ I_{\text{CoT}}^{D,h_\star}(\varepsilon; H) = \inf_{h \in \Delta_{\text{e2e}}^{D}(\varepsilon; H, h_\star)} \left\{ -\log P_{x \sim D}[h_{\text{CoT}}(x) = h_{\star}^{\text{CoT}}(x), \; h_{\text{e2e}}(x) = h_{\star}^{\text{e2e}}(x)] \right\}, \]
    其中 \(\Delta_{\text{e2e}}^{D}(\varepsilon; H, h_\star)\) 是端到端误差大于 \(\varepsilon\) 的假设集合。该值越大，说明CoT对区分坏假设越有效。
  - **上界定理**（以实可设定有限假设类为例）：CoT一致性学习规则的样本复杂度为
    \[ m = \frac{\log|H| + \log(1/\delta)}{I_{\text{CoT}}^{D,h_\star}(\varepsilon; H)}. \]
    相比于标准端到端监督的 \(\frac{\log|H|}{\varepsilon}\)，当 CoT 信息量远大于 \(\varepsilon\) 时，样本复杂度大幅降低。
  - **推广到无限类**：使用VC维数替代\(\log |H|\)，样本复杂度为
    \[ O\!\left( \left(\frac{1}{I_{\text{CoT}}}+1\right)\!\left( \text{VC}(L_{\text{CoT}}(H))\log\!\left(\frac{1}{I_{\text{CoT}}}+1\right)+\log\frac1\delta \right) \right). \]
  - **不可知（agnostic）设定**：定义不可知CoT信息 \(\tilde{I}_{\text{CoT}}^{D}(\varepsilon; H)\)，得到样本复杂度 \(O\!\left( \frac{\text{VC}(L_{\text{CoT}}(H))+\log(1/\delta)}{(\tilde{I}_{\text{CoT}})^2} \right)\)。
  - **下界定理**：使用Le Cam方法和Fano不等式证明，样本复杂度至少与 \(1/I_{\text{CoT}}\) 成比例，说明CoT信息量是刻画统计复杂度的基本量。
- **算法流程**：主要分析两类学习规则——**CoT一致性规则**（挑选训练样本上CoT完全一致的假设）和**CoT经验风险最小化**（最小化CoT损失）。理论证明它们的样本复杂度由CoT信息量决定。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **数据集与场景**：论文主要进行模拟实验，基于两种CoT假设类：
  - **确定性有限自动机（DFA）**：输入为固定长度字符串，输出为接受/拒绝，CoT为状态序列。
  - **迭代线性阈值模型**：模拟简单的自回归生成，窗口大小为8，迭代次数为16。
- **基准（benchmark）**：对比了**CoT一致性学习**与**标准端到端一致性学习**两种规则。
- **对比方法**：主要对比CoT-Cons和E2E-Cons的样本复杂度（达到相同端到端误差所需样本数）及学习曲线（正确率随样本量变化）。
- **评价指标**：端到端误差、经验学习曲线、CoT信息量与\(\varepsilon\)的比值等。

### 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点。

- **未明确说明**：论文属于理论性研究，实验部分为简单数值模拟，未提及具体的GPU型号、数量或训练时长。仅提到模拟在常规计算资源上完成，无需大型计算集群。

### 5. 实验数量与充分性：大概做了多少组实验（如不同数据集、消融实验等），这些实验是否充分、是否客观、公平。

- **实验数量**：
  - DFA实验：改变输入长度（2~10）、改变CoT详细程度（部分轨迹）、计算CoT信息量与\(\varepsilon\)的比值、绘制经验样本复杂度和学习曲线（图4中7个子图）。
  - 迭代线性阈值实验：展示成对假设的CoT信息量、信息量与端到端误差的比值、CoT信息函数、学习曲线、经验样本复杂度、正确率曲线（图5中6个子图）。
  - 转移学习实验：改变训练/测试分布长度（图7中2个子图）。
- **充分性**：实验覆盖了不同参数（长度、细节水平、混合监督），并验证了理论预测（如CoT信息量比值与样本复杂度改善的一致性）。实验设计客观，随机重复500次并展示置信区间，结果可靠。但所有实验均为模拟，未在真实LLM或大规模数据集上验证。

### 6. 论文的主要结论与发现

- **主要结论**：
  1. CoT监督的样本复杂度由CoT信息量 \(I_{\text{CoT}}\) 决定，而非传统的\(\varepsilon\)。当CoT高度信息时，样本复杂度可以远低于标准端到端监督。
  2. CoT信息量总是至少等于\(\varepsilon\)（实可设定），说明CoT监督信息论上永远不劣于端到端监督。
  3. 在不可知设定下，CoT信息量可能小于\(\varepsilon\)，此时CoT可能有害，需额外对齐假设类。
  4. 信息论下界证明CoT信息量是刻画学习速率的基本量。
- **发现**：自动机实验中，CoT信息量与\(\varepsilon\)的比值可达600倍，对应实际样本复杂度提升约2~3个数量级，理论与模拟高度吻合。

### 7. 优点：方法或实验设计上有哪些亮点。

- **理论创新**：首次提出“CoT信息量”这一概念，统一了CoT监督下的上界和下界，揭示了样本复杂度改善的根本原因——从每样本信息量（1/ε）提升为（1/ICoT）。
- **分析框架普适**：覆盖有限/无限假设类、实可/不可知设定、混合监督、转移学习等多种场景，提供统一工具。
- **模拟验证紧密**：通过DFA和线性阈值模型模拟，定量展示了CoT信息量比值与样本复杂度提升的高度一致，增强了理论的可信度。
- **下界证明严密**：结合Le Cam方法和Fano方法，分别针对ε依赖和假设空间大小两个维度给出下界，理论完备。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等。

- **实验覆盖有限**：仅做了简单假设类的模拟，未在真实自然语言任务（如数学推理、代码生成）上验证，缺少与现有LLM训练实践的对比。
- **理论假设较强**：假设输入分布独立同分布；假设误差度量是0-1损失；未考虑自回归生成中的概率性。实际LLM的CoT生成是自回归且非确定性，可能不符合文中的确定性假设类模型。
- **不可知设定风险**：文中指出当CoT假设类与数据不对齐时，CoT监督可能有害，但未给出如何自动检测或适应这种情形的算法。
- **缺少计算代价分析**：未讨论CoT标注成本、训练时间等实际工程因素。
- **应用限制**：结果主要针对PAC学习框架，对深度学习中常用的优化算法（如SGD、交叉熵损失）可能不直接适用。

（完）
