---
title: "AdaptiveStep: Automatically Dividing Reasoning Step through Model Confidence"
title_zh: 自适应步：通过模型置信度自动划分推理步骤
authors: "Yuliang Liu, Junjie Lu, Chaofeng Qu, Zhaoling Chen, Zefan Cai, Jason Klein Liu, Chonghan Liu, Yunhui Xia, Li Zhao, Jiang Bian, Chuheng Zhang, Wei Shen, Zhouhan Lin"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=ViRFgwVjk0"
tags: ["query:mm-cot"]
score: 7.0
evidence: 基于模型置信度划分推理步骤，用于步骤生成
tldr: 现有方法常基于规则（如固定长度或占位符）划分推理步骤，却忽略了真正决策点。AdaptiveStep根据模型预测下一token时的置信度来动态划分步骤，提供更丰富的决策信息，无需人工标注。实验表明，该方法在数学推理和代码生成任务上提升了过程奖励模型的训练效果，为推理步骤的自动划分提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-virfgwvjk0/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 848, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-virfgwvjk0/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1737, \"height\": 729, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-virfgwvjk0/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1778, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-virfgwvjk0/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1783, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-virfgwvjk0/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 901, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-virfgwvjk0/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 894, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-virfgwvjk0/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1788, \"height\": 1517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-virfgwvjk0/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1775, \"height\": 755, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-virfgwvjk0/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1429, \"height\": 921, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-virfgwvjk0/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1752, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-virfgwvjk0/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 679, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-virfgwvjk0/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 622, \"height\": 452, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-virfgwvjk0/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 633, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-virfgwvjk0/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 817, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-virfgwvjk0/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 847, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-virfgwvjk0/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1789, \"height\": 597, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-virfgwvjk0/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1788, \"height\": 597, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-virfgwvjk0/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1825, \"height\": 906, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-virfgwvjk0/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1250, \"height\": 160, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-virfgwvjk0/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1519, \"height\": 530, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-virfgwvjk0/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1555, \"height\": 1100, \"label\": \"Table\"}]"
motivation: 现有推理步骤划分方法常忽视真正决策点，导致步骤定义不准确。
method: 提出基于模型预测下一词置信度的步长划分方法，自适应确定决策点。
result: 在数学推理和代码生成任务上，自适应步训练的过程奖励模型表现更优。
conclusion: 自适应步无需人工标注即可自动划分推理步骤，提升下游任务效果。
---

## Abstract
Current approaches for training Process Reward Models (PRMs) often involve deconposing responses into multiple reasoning steps using rule-based techniques, such as using predefined placeholder tokens or setting the reasoning step's length to a fixed size.
These approaches overlook the fact that certain words don't usually indicate true decision points. To address this, we propose AdaptiveStep, a method that divides reasoning steps based on the model's confidence in predicting the next word, offering more information on decision-making at each step, improving downstream tasks like reward model training. Moreover, our method requires no manual annotation. 
Experiments with AdaptiveStep-trained PRMs in mathematical reasoning and code generation show that the outcome PRM achieves state-of-the-art Best-of-N performance, surpassing greedy search strategy with token-level value-guided decoding, while also reducing construction costs by over 30% compared to existing open-source PRMs. We also provide a thorough analysis and case study on its performance, transferability, and generalization capabilities. We provide our code on https://github.com/Lux0926/ASPRM.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

*   **核心问题**：当前训练过程奖励模型（PRM）时，通常采用基于规则的方法（如固定符号换行、固定token长度）将模型回答分解为多个推理步骤。这些方法忽略了推理过程中真正的决策点，导致步骤划分粗糙、信息量低，限制了PRM在下游任务（如最佳N选一、引导解码）中的性能。此外，规则方法在代码生成等难以明确定义步骤的领域应用困难。
*   **整体含义**：为克服上述局限，本文提出**AdaptiveStep**——一种自动、高效、通用且信息量丰富的推理步骤划分方法。其核心思想是利用模型在预测下一个token时的**置信度**来识别关键决策点，从而将回答划分为更符合认知过程的步骤。该方法无需人工标注，可应用于数学推理与代码生成等复杂推理任务，并显著提升PRM的训练效率与下游性能。

### 2. 论文提出的方法论：核心思想、关键技术细节

*   **核心思想**：模型在生成回答时，预测token的概率（置信度）反映了其决策的“困难”程度。低置信度的token位置往往代表了真正的推理决策点（如计算中间结果、选择运算对象等）。因此，以这些位置作为步骤边界，可以得到比规则划分更具信息量的推理步骤。
*   **关键技术细节**：
    1.  **步骤划分（AdaptiveStep）**：
        *   给定问题 \( q \)，用语言模型 \( \pi \) 采样 \( N \) 个回答。
        *   计算每个token \( s_{n}^{i} \) 的置信度 \( c_{s_{n}^{i}} = p(s_{n}^{i} \mid \pi, q, s_{n}^{<i}) \)（即模型预测该token的概率）。
        *   设定阈值 \( \tau \)（本文取2%，源于认知心理学中深度思考约占总思考时间2%的论断）。将置信度低于 \( \tau \) 的token位置作为断点，从而将回答 \( s_{n} \) 划分为 \( K \) 个推理步骤 \( s_{n} = \{r_{1}, r_{2}, ..., r_{K}\} \)。每个步骤的最后一个token是低置信度点。
    2.  **PRM训练**：
        *   **目标奖励估计**：对每个划分好的步骤 \( r_{k} \)，从该步骤开始向后进行 \( J \) 次 rollout（续写），判断是否至少有一条路径能到达正确答案（硬估计HE）。若存在正确路径，则步骤奖励 \( re_{k}=1 \)，否则 \( re_{k}=0 \)。
        *   **损失函数**：使用二元交叉熵损失训练PRM \( R_{\theta} \)：  
            \[
            L_{\theta}^{PRM} = -\sum_{k=1}^{K} \left( re_{k} \log r_{\theta}^{k} + (1 - re_{k}) \log(1 - r_{\theta}^{k}) \right)
            \]
            其中 \( r_{\theta}^{k} = R_{\theta}(p, r_{1}, ..., r_{k}) \) 是PRM对该步骤的预测得分。
    3.  **Token级值引导解码（TVD）**：
        *   在推理时，当模型遇到低置信度token（Top-1概率 \( c_{p} < \tau \)），则触发PRM对概率最高的 \( M \) 个候选token进行评估，选择PRM评分最高的token作为最终输出。

### 3. 实验设计：数据集 / 场景、Benchmark、对比方法

*   **数据集**：
    *   **数学推理**：训练集使用 MetaMathQA；测试集使用 GSM8k 和 MATH500。此外，使用 GSM-Symbolic (p2) 进行域内泛化测试。
    *   **代码生成**：自建 LeetCodeDataset（1940题，含训练1745题、测试175题，问题来自LeetCode，答案来自开源仓库，测试用例手动收集）；另使用 LiveCodeBench-V4 作为在线评测。
*   **场景**：BoN（Best-of-N）选择（用PRM为N个候选评分，选最优）和 TVD（将PRM嵌入解码过程直接引导生成）。
*   **对比方法**：
    *   **数学领域**：Math-Shepherd、ER-PRM（均使用相同基模型的PRM）。
    *   **代码领域**：由于开源可用的代码PRM有限，仅训练了一个代码ORM作为基线（仅用最终答案评分）。
*   **模型设置**：
    *   **策略模型**：数学：MetaMath-Mistral（基于Mistral-V0.1）和 MetaMath-Llama（用于迁移性实验）；代码：LCD-DS（基于DeepSeek-Coder-Base）。
    *   **PRM基座**：数学：ASPRM-L（基于Llama-3.1-8B）和 ASPRM-M（基于Mistral-V0.1）；代码：ASPRM-D（基于DeepSeek-Coder-Base）。
*   **评估指标**：在BoN中，用PRM对每个候选的最小步骤得分作为最终分；在TVD中，直接计算准确率（数学）或Pass@1（代码）。

### 4. 资源与算力

*   论文**未明确说明**使用的GPU型号、数量、总训练时长等具体算力信息。
*   仅提及**数据构建成本**相比于 Math-Shepherd 和 ER-PRM **降低了超过30%**，因为ASPRM只用单一策略模型、更少的采样次数（30次/问题）和更少的rollout（8次/步骤）。

### 5. 实验数量与充分性：实验设置、公平性

*   **实验数量**：较为充分。包含：
    *   BoN实验：数学领域4组（不同基模型×2数据集）、代码领域2组。
    *   TVD实验：1个汇总表（表1），涵盖数学和代码共6个设定。
    *   **消融/分析实验**：
        *   迁移性（表2）
        *   评分位置泛化（表3，含置信度、随机、硬分割三种设置）
        *   域内泛化（表4，使用GSM-Symbolic）
        *   跨域泛化（表5）
        *   混合数据训练（表6）
        *   阈值分析（图6，0.5%、1%、1.5%、2%四种阈值）
        *   特征统计（附录A.1，详列决策token在各类词汇/符号中的占比）
        *   训练数据分布分析（图9，检查困难问题是否被过度分割）
        *   案例研究（附录表11-12）。
*   **公平性与充分性**：实验设计较客观。数学领域与两种主流PRM对比，代码领域因缺乏开源PRM而与ORM对比。实验中控制了基模型、训练数据源、构建成本等变量。但在代码领域缺乏与其他PRM的直接对比，是一个局限性。总体而言实验覆盖了多个维度的验证，充分性中等偏上。

### 6. 论文的主要结论与发现

*   AdaptiveStep方法能自动、高效地划分出信息量丰富的推理步骤，显著优于规则划分。
*   ASPRM在数学BoN上达到SOTA，尤其在GSM8k上ASPRM-L表现最佳。
*   在TVD评估中，ASPRM显著优于贪婪解码（数学：GSM8k +3.15%，MATH500 +14.4%；代码：LeetCode +6.54%，LiveCodeBench +3.70%），而Math-Shepherd和ER-PRM有时反而导致性能下降。
*   ASPRM具有**模型迁移性**（但有限）、**评分位置泛化**（在随机划分点也能保持一定效用）、**域内泛化**（在GSM-Symbolic上有效）以及**跨域泛化**（数学PRM能部分用于代码，代码PRM在困难数学任务上也有提升）。
*   **混合不同领域数据**（数学+代码）训练可进一步提升PRM性能，尤其是在困难数学任务上。
*   特征分析表明，低置信度点**非均匀分布**：数学计算、连词选择、代码注释中的计划阶段是主要决策点，而换行符等规则断点很少是真正决策点。

### 7. 优点：方法或实验设计上的亮点

*   **方法创新**：跳出规则框架，利用模型本身置信度自动识别真正的推理决策点，这一思路简洁且符合认知直觉。
*   **自动化与低成本**：无需人工标注步骤，数据构建成本比现有开源PRM降低30%以上。
*   **通用性强**：可无缝应用于数学和代码两类不同领域的推理任务，且跨域泛化实验显示一定普适性。
*   **实际效益**：TVD将PRM直接嵌入解码过程，不增加额外推理开销，却能带来显著性能提升，具有实用价值。
*   **开源与可复现**：公开了代码、数据集（LeetCodeDataset）和模型，有利于社区验证与后续研究。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制

*   **实验覆盖的局限**：
    *   代码领域仅与ORM对比，缺乏与其他PRM（如基于规则划分的PRM）的直接比较，说服力稍弱。
    *   未在更大规模模型（如70B级别）或更多样化任务（如多轮对话推理、科学问答）上验证，难以断言泛化至所有复杂推理场景。
*   **偏差风险**：
    *   阈值2%的设定基于心理学文献，但图6显示不同能力模型的最优阈值可能不同，论文未完全解决自适应阈值问题。
    *   数据构建依赖单一策略模型，迁移性实验显示用强模型数据训练弱模型PRM效果下降，可能存在模型能力不匹配的风险。
*   **应用限制**：
    *   TVD在解码过程中需要实时调用PRM，可能增加延迟（尤其在低频决策点较多时），论文未量化额外时间开销。
    *   特征分析中低置信度点的分类依赖于词性标注工具，可能存在标注偏差。
*   **其他**：算力消耗未详细报告，可能影响其他研究者复现时的成本估算。

（完）
