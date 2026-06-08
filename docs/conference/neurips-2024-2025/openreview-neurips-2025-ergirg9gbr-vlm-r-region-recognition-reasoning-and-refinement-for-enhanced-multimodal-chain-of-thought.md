---
title: "VLM-R³: Region Recognition, Reasoning, and Refinement for Enhanced Multimodal Chain-of-Thought"
title_zh: VLM-R³：通过区域识别、推理与精炼增强多模态链式推理
authors: "Chaoya Jiang, Yongrui Heng, Wei Ye, Haiyang Xu, Ming Yan, Ji Zhang, Fei Huang, Shikun Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ERGIrG9GBR"
tags: ["query:mm-cot"]
score: 9.0
evidence: 通过区域识别和精炼增强多模态链式推理
tldr: 现有的多模态推理模型生成文本推理链时缺乏动态视觉接地，导致推理与视觉证据脱节。论文提出VLM-R³框架，赋予模型决定何时需要视觉证据、在图像中定位相关区域、并将子图内容无缝融入链式推理的能力。该方法通过区域条件强化学习训练，在复杂视觉推理任务上显著提升链式推理的准确性和可解释性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ergirg9gbr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 651, \"height\": 867, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ergirg9gbr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1288, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ergirg9gbr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 586, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ergirg9gbr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1374, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ergirg9gbr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1392, \"height\": 1101, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ergirg9gbr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1413, \"height\": 879, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ergirg9gbr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1414, \"height\": 879, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ergirg9gbr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1295, \"height\": 1097, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ergirg9gbr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1189, \"height\": 921, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ergirg9gbr/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1186, \"height\": 1134, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ergirg9gbr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1464, \"height\": 835, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ergirg9gbr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1346, \"height\": 629, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ergirg9gbr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1394, \"height\": 319, \"label\": \"Table\"}]"
motivation: 多模态链式推理缺乏动态视觉接地，难以在推理中准确引用视觉区域。
method: 提出框架使模型具备区域识别、推理和精炼能力，利用区域条件强化学习训练。
result: 在需细粒度视觉推理的任务上，链式推理的准确率和接地精度大幅提升。
conclusion: 区域级别的视觉接地显著增强了多模态链式推理的可靠性和可解释性。
---

## Abstract
Recently, reasoning-based MLLMs have achieved a degree of success in generating long-form textual reasoning chains. However, they still struggle with complex tasks that necessitate dynamic and iterative focusing on and revisiting of visual regions to achieve precise grounding of textual reasoning in visual evidence. We introduce VLM-R³  (Visual Language Model with Region Recognition, Reasoning, and Refinement ), a framework that equips an MLLM with the ability to (i) decide when additional visual evidence is needed, (ii) determine where to ground within the image, and (iii) seamlessly weave the relevant sub-image content back into an interleaved chain-of-thought. The core of our method is \textbf{Region-Conditioned Reinforcement Policy Optimization (R-GRPO)}, a training paradigm that rewards the model for selecting informative regions, formulating appropriate transformations (e.g. crop, zoom), and integrating the resulting visual context into subsequent reasoning steps. To bootstrap this policy, we compile a modest but carefully curated Visuo-Lingual Interleaved Rationale (VLIR) corpus that provides step-level supervision on region selection and textual justification. Extensive experiments on MathVista, ScienceQA, and other benchmarks show that VLM-R$^3$ sets a new state of the art in zero-shot and few-shot settings, with the largest gains appearing on questions demanding subtle spatial reasoning or fine-grained visual cue extraction.

---

## 论文详细总结（自动生成）

# VLM-R³ 论文总结

## 1. 核心问题与整体含义（研究动机和背景）

近年来，基于推理的多模态大语言模型（MLLM）在生成长篇文本推理链方面取得了一定成功。然而，这些模型在处理需要动态、迭代地关注和重新审视视觉区域的复杂任务时仍显不足。现有链式推理（CoT）方案大多将推理步骤局限于文本域，仅在初始阶段对视觉输入进行一次性接地，无法在后续推理过程中持续与特定视觉区域交互。例如，顺序验证假设、追踪对象状态、理解复杂空间关系等任务，都需要更主动、自适应的视觉接地机制。为此，论文提出 **VLM-R³** 框架，赋予模型三项能力：（1）判断何时需要额外视觉证据；（2）确定在图像中聚焦的位置；（3）将相关子图内容无缝融入交错的推理链中，从而实现精确的视觉证据接地。

## 2. 方法论

### 核心思想
VLM-R³ 采用“区域识别—推理—精炼”的循环过程：在推理过程中，模型可自主决定裁剪（crop）并放大图像特定区域，将获取的局部视觉信息追加到上下文序列中，继续生成推理文本或新的裁剪指令，直至输出最终答案。这一过程模拟了人类“再观察—再推理”的认知行为。

### 关键技术细节

- **Visuo-Lingual Interleaved Rationale (VLIR) 数据集**：为冷启动监督微调而构建，包含 11,810 个样本，来源包括 GQA、TextVQA、DocVQA、InfographicsVQA、VSR 等。每个样本提供交错排列的文本推理步骤、区域定位（边界框）及对应的裁剪图像。数据通过强大的 MLLM（如 Qwen2.5-VL 72B、GPT-4o）经提示生成，并经过语义单位有效性和推理逻辑一致性双重过滤。

- **交互式推理管道**：模型按指令格式（如 `{"bbox_2d": [x1, y1, x2, y2]}`）生成裁剪指令时，系统解析坐标并执行裁剪操作，将得到的放大子图编码为视觉令牌追加到输入序列中，随后模型继续生成。此循环持续至模型生成 `<answer>...</answer>` 结束。

- **Region-Conditioned Reinforcement Policy Optimization (R-GRPO)**：基于 Group Relative Policy Optimization (GRPO) 的强化学习策略。关键公式如下：
  - 优势估计：  
    \[
    \hat{A}_i = \frac{r_i - \text{mean}(\{r_1,\dots,r_M\})}{\text{std}(\{r_1,\dots,r_M\})}
    \]
  - 损失函数（含 KL 散度约束）：  
    \[
    \mathcal{L}_{\text{GRPO}} = -\mathbb{E}_{Q \in \mathcal{D}_S} \left[ \sum_{i=1}^M \frac{\pi_\theta(c_i|Q)}{\pi_{\text{ref}}(c_i|Q)} \hat{A}_i - \beta D_{\text{KL}}(\pi_\theta \| \pi_{\text{ref}}) \right]
    \]
  - 奖励总分为四项之和：准确性奖励（终端，正确为1）、格式奖励（终端，标签正确为1）、区域有效性奖励（中间，每个有效边界框0.5，上限0.5，仅在答案正确时给予）、推理长度奖励（中间，每字符0.001，上限0.25）。训练时仅对模型生成的文本令牌和边界框令牌计算策略梯度，注入的图像令牌不参与梯度更新。

## 3. 实验设计

### 数据集与基准
- **通用视觉语言理解**：MME、MMMU  
- **复杂数学推理**：MathVista、MathVision  
- **科学问答**：ScienceQA  
- **文档理解**：DocVQA  
- **幻觉检测**：HallusionBench  
- **视觉中心基准**：MMVP、V*、HR-Bench、MME-Realworld

### 对比方法
- **开源非推理模型**：Qwen2.5-VL 7B（基线）、InternVL2.5-8B、LLaVA-Next 8B  
- **闭源非推理模型**：Gemini-2 Flash、GPT-4o  
- **开源推理模型**：LLaVA-CoT 11B、Mulberry-Qwen2VL 7B、R1-onevision 7B、Vision-R1 7B  
- **更大闭源模型**：o1

### 实验设置
- 主实验（Table 1）在 7 个基准上对比。  
- 视觉中心基准（Table 2）在 5 个任务上对比，并与多组基线（如 LLaVA-OneVision-72B、InternVL3-38B）及本文消融变体比较。  
- 消融实验（Table 3）在 MathVista、MMMU、ScienceQA、DocVQA 上分别去除组件。  
- 额外分析：区域接地准确率影响（图4，从 40% 至 90% 模拟）、注意力分布可视化（图5）。

## 4. 资源与算力

- **监督微调阶段**：4 块 NVIDIA A100 80GB GPU，使用 DeepSpeed，batch size=2，梯度累积=8，学习率 2×10⁻⁷，训练 3 个 epoch。仅训练 LLM 部分，视觉编码器和 MLP 投影器冻结。
- **R-GRPO 阶段**：6 块 NVIDIA A100 80GB GPU，batch size=1 per device，梯度累积=16，学习率 1×10⁻⁶，训练 300 步。同样仅训练 LLM。

## 5. 实验数量与充分性

论文进行了多组实验：
- 主实验（Table 1）覆盖 7 个基准，与超过 10 种基线对比。  
- 视觉中心专用实验（Table 2）覆盖 5 个基准，包含多种消融变体（纯文本RL、纯文本边界框、完整图像重插入等）。  
- 组件消融实验（Table 3）在 4 个基准上分别移除交错推理、VLIR 微调、R-GRPO，量化各组件贡献。  
- 区域接地准确率影响分析（图4）覆盖 3 个基准，5 个准确率水平。  
- 注意力分布对比（图5）提供定性分析。

实验设计较为全面，涵盖了不同难度和领域的推理任务，消融实验分离了关键组件的影响，对比基线涵盖了当前主流方法，结果统计具有可比性。总体上实验充分且客观。

## 6. 主要结论与发现

1. **VLM-R³ 在多个基准上显著优于基线**，尤其在需要细粒度视觉推理的任务上提升明显：  
   - ScienceQA 提升 14.33%（87.9% vs. 73.6%）  
   - MathVision 提升 5.1%（30.2% vs. 25.1%）  
   - MathVista 提升 2.2%（70.4% vs. 68.2%）  
   - 视觉中心基准平均得分 70.1%，超过基线 Qwen2.5-VL 的 63.5%。

2. **交错推理链（Interleaved CoT）至关重要**：去掉裁剪图像仅保留文本边界框描述，性能普遍下降（ScienceQA -12.5%，MMMU -2.8%），且不如完整交错方案。

3. **VLIR 微调是有效冷启动**：跳过 VLIR 直接进行 R-GRPO 导致性能大幅下降（ScienceQA -15.7%），并破坏指令遵循能力。

4. **R-GRPO 进一步优化策略**：相比仅 SFT，R-GRPO 在 ScienceQA 上再提升 3.28%，在 MathVista 上提升 0.7%。

5. **区域接地准确率与最终性能高度正相关**，准确率从 40% 提升至 90% 时，ScienceQA 从 54.1% 升至 87.9%，说明精确的区域定位是有效推理的基础。

6. **交错推理保持视觉注意力持久**：注意力热图显示，后续推理令牌与裁剪区域保持强连接，而传统方法中视觉注意力随推理链衰减。

## 7. 优点

- **方法创新性强**：首次将动态区域接地与交错链式推理结合，提出 VLIR 数据集和 R-GRPO 训练范式，赋予模型自主决定“何时、何地、如何”获取视觉证据的能力。  
- **实验全面且设计严谨**：覆盖多个领域和难度的基准，包含丰富的消融与对比实验，定量和定性分析兼有。  
- **结果显著且可解释**：在 ScienceQA 等细粒度推理任务上取得大幅提升，并通过注意力分布和接地准确率分析解释了有效性。  
- **开源透明**：基于 Qwen2.5-VL 7B 构建，完整披露训练配置和数据集构建细节，便于复现。

## 8. 不足与局限

- **数据集规模较小**：VLIR 仅含 11,810 样本，可能限制泛化能力；R-GRPO 阶段仅用 ~5,000 样本、300 步训练，可能未充分收敛。  
- **数据构建成本高**：依赖 Qwen2.5-VL 72B 和 GPT-4o 等昂贵模型生成中间数据，且需人工设计提示，可扩展性受限。  
- **仅使用 7B 模型**：未验证更大参数规模下的性能与效率，结论可能受模型容量影响。  
- **区域接地准确率敏感**：性能随接地质量下降而快速退化，实际应用中若定位不准将严重影响结果。  
- **操作类型有限**：仅支持 crop 和 zoom 两种转换，缺乏更丰富的视觉操作（如旋转、颜色增强等）。  
- **未讨论偏差与公平性**：没有分析模型在敏感场景下的潜在风险或数据偏差。  
- **缺少专门的局限性章节**：论文未明确列出局限，需从实验和设置中推断。

（完）
