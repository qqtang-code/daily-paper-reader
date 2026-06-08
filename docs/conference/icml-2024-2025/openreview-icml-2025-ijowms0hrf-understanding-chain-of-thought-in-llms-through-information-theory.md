---
title: Understanding Chain-of-Thought in LLMs through Information Theory
title_zh: 通过信息论理解大语言模型中的链式思维
authors: "Jean-Francois Ton, Muhammad Faaiz Taufiq, Yang Liu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=IjOWms0hrf"
tags: ["query:mm-cot"]
score: 7.0
evidence: 通过信息论分析链式思维推理
tldr: 现有CoT评估方法需要标注数据或无法准确评估中间步骤。本文从信息论角度形式化CoT推理，通过量化每一步的信息增益来识别模型失败模式，无需昂贵的标注数据集。在玩具算术等任务上验证了方法的有效性，为CoT评估提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 197, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 796, \"height\": 263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1654, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 554, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1031, \"height\": 2095, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1044, \"height\": 2096, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1042, \"height\": 2091, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 888, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 886, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ijowms0hrf/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 889, \"height\": 444, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ijowms0hrf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 441, \"height\": 177, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ijowms0hrf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1714, \"height\": 451, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ijowms0hrf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1024, \"height\": 239, \"label\": \"Table\"}]"
motivation: 现有链式思维评估方法依赖标注数据或存在高误报率的问题。
method: 提出信息论框架，量化推理步骤中的信息增益，识别失败模式。
result: 在玩具算术任务上验证了该方法无需标注即可有效评估CoT质量。
conclusion: 信息论视角为理解CoT推理提供了一种无标注的评估工具。
---

## Abstract
Large Language Models (LLMs) have shown impressive performance in complex reasoning tasks through the use of Chain-of-Thought (CoT) reasoning, allowing models to break down problems into manageable sub-tasks. However, existing CoT evaluation techniques either require annotated CoT data or fall short of accurately assessing intermediate reasoning steps, leading to high rates of false positives. In this paper, we formalize CoT reasoning in LLMs through an information-theoretic lens. Specifically, our framework quantifies the `information gain' at each reasoning step, enabling the identification of failure modes in LLMs without the need for expensive annotated datasets. We demonstrate the efficacy of our approach through extensive experiments on toy arithmetic, GSM8K and PRM800k datasets, where it significantly outperforms existing outcome-based methods by providing more accurate insights into model performance on individual tasks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：大型语言模型（LLM）通过链式思维（Chain-of-Thought, CoT）推理显著提升了复杂任务能力，但现有CoT评估方法存在两大缺陷：① 依赖昂贵的人工标注中间步骤（如过程监督）；② 仅基于最终结果（outcome-based）的方法（如ORM、Math-Shepherd）容易受虚假相关影响，导致高误报率（false positive），无法准确识别错误推理步骤。
- **整体含义**：本文旨在探索一种无需标注中间步骤的CoT评估框架，通过信息论量化每个推理步骤对最终正确答案的“信息贡献”，从而自动识别模型在哪个子任务上失败，为模型优化提供细粒度指导。

## 2. 论文提出的方法论
### 核心思想
- 每一步正确的推理都应该提供有助于预测最终正确答案的**信息**。若某步骤未增加信息，则说明该步骤可能错误或不可靠。
- 通过条件互信息 \(I(Y; X_t \mid X_{t-1})\) 衡量步骤 t 的**信息增益（Information Gain, IG）**，其中 \(Y\) 是真实最终答案，\(X_t\) 是模型推理到步骤 t 的状态。
- **理论支撑**：若某子任务在训练数据中不可识别（即模型无法通过已学原语任务组合实现），则后续所有步骤的信息增益应为零（定理3.3）。

### 关键技术细节
1. **形式化框架**：
   - 定义初始状态 \(X_0\)、任务 \(\lambda\)（可分解为原语子任务序列 \(\lambda_1 \circ \cdots \circ \lambda_T\)）。
   - 模型执行任务 \(\lambda\) 得到状态序列 \(X_0, X_1^M, \dots, X_T^M\)，最终输出 \(Y^M\)。
   - 引入**不可识别性**：若某子任务不在训练数据的原语任务张成空间中，模型无法正确执行。

2. **信息增益估计**：
   - 利用命题3.4：\(I(Y; X_t \mid X_{t-1}) = \mathbb{E}[\log p(Y \mid X_t)] - \mathbb{E}[\log p(Y \mid X_{t-1})]\)。
   - 训练一个**监督模型** \(g_{\text{sup}}\)，以中间步骤为输入，直接预测真实答案 \(Y\)，用交叉熵损失近似 \(\log p(Y \mid X_t)\)。
   - 信息增益 ≈ \(\mathbb{E}[\ell_{\text{CE}}(Y, g_{\text{sup}}(X_{t-1}))] - \mathbb{E}[\ell_{\text{CE}}(Y, g_{\text{sup}}(X_t))]\)。

3. **样本级信息增益**：
   - 对于单个推理轨迹，定义 \(\log p(Y \mid X_t) - \log p(Y \mid X_{t-1})\)，正值表示步骤正确（增加信心），非正值表示步骤错误或无关。
   - 可推广到O1/R1式回溯推理：错误路径的低增益、自我修正后的高增益仍可被捕获。

### 算法流程（文字说明）
1. 收集包含最终正确答案的CoT推理数据。
2. 对每条推理链，在不同截断点（步骤0,1,…,T）构造输入-输出对（输入为截至该步的推理文本，输出为正确答案）。
3. 用这些数据微调一个监督模型（如GPT-2或LoRA调优的Llama-8B），使其能根据部分推理预测正确答案。
4. 计算每个步骤的聚合信息增益（平均样本级增益），或样本级增益。
5. 若某步骤信息增益显著降低或为负，则标记为该步骤执行错误。

## 3. 实验设计
- **数据集/场景**：
  1. **玩具算术**：5步自定义数学任务（向量变换），人为在特定步骤引入随机错误（两种模式：随机50%错误、条件错误）。
  2. **Llama-3-8B算术**：计算 \(3x, 2y, 3x+2y\)，x,y均匀采样于[1,10^5)，大多数错误出现在第三步加法。
  3. **GSM8K控制实验**：用GPT-4生成CoT，人为使所有乘法步骤错误，并确保错误最终答案同时包含乘法和减法，引入减法与错误答案的虚假相关。
  4. **PRM800K**：MATH数据集的人工地步标签（+1正确，-1错误，0中性），评估自然错误检测。
- **基准方法**：
  - **Outcome Reward Model (ORM)**：训练分类器预测最终答案正确概率。
  - **Math-Shepherd (MS)**：从各步骤开始用同一模型生成多条完成轨迹，以正确完成比例评估步骤质量。
- **评估指标**：准确率（ACC）、真阳性率（TPR）、假阳性率（FPR），以及聚合信息增益/概率值。

## 4. 资源与算力
- **文中未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。
- 仅提到在玩具实验中使用了GPT-2作为监督模型，在Llama-3-8B实验中使用了LoRA微调，在PRM800K中也使用了GPT-2 SFT。但未披露训练时间、硬件配置等细节。
- **需指出**：论文未提供资源与算力细节。

## 5. 实验数量与充分性
- **实验组数**：共4个主要实验场景（玩具实验包含5个子模型共5组对比、Llama-3-8B、GSM8K、PRM800K）。每个实验均报告聚合指标和样本级检测指标。
- **充分性**：覆盖了合成数据、真实模型、带控制混淆的数据集、自然标注数据集；对比了两种主流基线方法；报告了ACC、TPR、FPR等详细指标。实验设计较为全面，尤其通过GSM8K控制了虚假相关突出本文方法优势。
- **公正性**：基线方法设置公平（MS使用相同模型作为完成器；ORM数据与本文方法相同）。但缺少与更先进的过程监督方法（如PRM）的直接对比（由于PRM需要标注，本文未对比）。总体实验客观、有说服力。

## 6. 论文的主要结论与发现
- 提出的信息增益方法能**准确识别CoT中错误的子任务**，且无需任何人工标注中间步骤。
- 在玩具数据中，ORM和MS在条件错误场景（LLM 3）下失败（误判错误步骤），而信息增益始终保持正确。
- 在Llama-3-8B算术中，ORM和MS因受输入变量分布影响而无效，信息增益能正确识别第三步加法为主要错误点。
- 在GSM8K控制实验中，ORM因虚假相关错误地将减法标记为错误，信息增益正确识别乘法为唯一错误。
- 在PRM800K上，信息增益与人类标注高度一致（负/中性步骤信息增益低或负，正步骤增益高），而ORM几乎无区分力。
- 样本级检测中，信息增益在所有数据集上ACC、TPR均优于或等于ORM和MS，且FPR显著更低。

## 7. 优点
- **无需标注中间步骤**：仅需最终正确答案即可评估每一步推理质量，极大降低人力成本。
- **理论严谨**：基于信息论（条件互信息）给出正式定义和定理，保证方法的可解释性。
- **鲁棒性强**：能处理复杂推理模式（如回溯、自我修正），且对虚假相关不敏感。
- **实用性高**：方法通用，可应用于不同领域（数学、逻辑等），且与模型无关。

## 8. 不足与局限
- **计算开销**：需要训练一个额外的监督模型（supervisor model），虽然避免了人工标注但引入了训练成本。
- **步骤分类依赖**：虽然不需要标注每一步的正确性，但仍需将推理步骤归类到对应子任务（如“加法”“乘法”），这在某些领域（如常识问答）可能不直观。
- **实验覆盖有限**：主要聚焦数学/算术任务，未在更多领域（如Blocks World、常识推理）验证；也未与最新过程监督方法（如PRM）进行直接对比（只对比了ORM和MS）。
- **资源细节缺失**：未报告训练监督模型的具体算力需求，不利于复现和成本评估。
- **假设限制**：依赖于“正确步骤应增加信息”的假设，若模型进行无意义但统计上偶然正确的推理，可能产生误判（论文已讨论但未完全解决）。
- **未讨论多模型集成或校准**：监督模型本身可能引入偏差，文中未进行监督模型选择或校准分析。

（完）
