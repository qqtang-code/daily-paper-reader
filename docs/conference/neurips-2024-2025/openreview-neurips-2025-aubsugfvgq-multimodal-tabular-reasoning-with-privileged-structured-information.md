---
title: Multimodal Tabular Reasoning with Privileged Structured Information
title_zh: 利用特权结构化信息的多模态表格推理
authors: "Jun-Peng Jiang, Yu Xia, Hai-Long Sun, Shiyin Lu, Qing-Guo Chen, Weihua Luo, Kaifu Zhang, De-Chuan Zhan, Han-Jia Ye"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=AuBSUgFVgq"
tags: ["query:multimodal"]
score: 8.0
evidence: 利用特权信息的多模态表格推理
tldr: 该论文处理直接从表格图像进行多步推理的任务。核心策略是在训练时利用特权结构化信息（真实表格数据），但在测试时仅用图像。通过视觉-结构化对齐和多步推理，显著提升多模态表格推理性能。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-aubsugfvgq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 691, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aubsugfvgq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 703, \"height\": 267, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aubsugfvgq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 862, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aubsugfvgq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1414, \"height\": 550, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-aubsugfvgq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1394, \"height\": 530, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-aubsugfvgq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 490, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aubsugfvgq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 537, \"height\": 493, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aubsugfvgq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1435, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aubsugfvgq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 880, \"height\": 638, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aubsugfvgq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1392, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aubsugfvgq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1016, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aubsugfvgq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 243, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-aubsugfvgq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 740, \"height\": 177, \"label\": \"Table\"}]"
motivation: 现实场景中表格常以图像形式出现，缺乏高质量文本表示，难以进行复杂推理。
method: 在训练时引入真实表格数据作为特权信息，辅助视觉对齐和多步推理。
result: 在表格图像推理任务上显著优于基线模型。
conclusion: 特权结构化信息能有效增强多模态模型在表格推理中的表现。
---

## Abstract
Tabular reasoning requires complex, multi-step information extraction and logical inference, such as aggregation, comparison, or calculation over tabular data. While recent advances have leveraged large language models (LLMs) for reasoning over structured text tables, such high-quality textual representations are often unavailable in real-world settings, where tables typically appear as images. In this paper, we tackle the task of tabular reasoning directly from table images. Our core strategy is to leverage privileged structured information---specifically, the ground-truth structured table data available during training but inaccessible at test time---to enhance multimodal large language models (MLLMs). The key challenges lie in: accurately aligning visual representations with the structured information, particularly mapping the visual evidence to logical steps; and effectively transferring the reasoning skills learned during training to the MLLM for visual inference. 
To address these, we introduce {\sc Turbo} (TabUlar Reasoning with Bridged infOrmation), a new framework for multimodal tabular reasoning using privileged information. {\sc Turbo} benefits from a structure-aware reasoning trace generator based on DeepSeek-R1, which contributes to high-quality modality-bridged information. On this basis, {\sc Turbo} repeatedly generates and selects advantageous reasoning traces, further enhancing the model's tabular reasoning ability. Experimental results demonstrate that, with limited (9k) data, {\sc Turbo} achieves state-of-the-art performance ($+7.2\%$ vs. previous SOTA) across multiple datasets.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 一、论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：现实场景中表格通常以图像或截图形式出现，难以获取高质量的文本/结构化表示（如 Markdown 表格）。现有的多模态大语言模型（MLLMs）在图像表格推理任务上面临挑战，难以有效提取视觉信息并进行多步逻辑推理（如聚合、比较、计算）。

- **核心问题**：如何在训练阶段利用训练时可用但测试时不可获取的“特权结构化信息”（即真实表格数据）来增强 MLLMs 在仅依赖表格图像时的推理能力？主要挑战包括：（1）准确将视觉表示与结构化信息对齐，尤其是将视觉证据映射到逻辑步骤；（2）将训练中习得的推理技能有效迁移到视觉推理场景中。

- **整体含义**：论文提出了 TURBO（TabUlar Reasoning with Bridged infOrmation）框架，通过特权结构化信息桥接模态差异，在有限数据（9k）下显著提升多模态表格推理性能，达到新 SOTA（+7.2%）。

### 二、论文提出的方法论

- **核心思想**：利用结构感知的推理轨迹作为“桥接信息”，将结构化表格（Markdown）与表格图像之间的模态差异弥合，使 MLLM 学会从图像中推理。采用两阶段训练：监督微调（SFT）+ 强化学习（RL）。

- **关键技术细节**：

  1. **结构感知推理轨迹生成**：将结构化 Markdown 表格、问题、答案输入 DeepSeek-R1（SOTA 推理 LLM），生成高质量的推理轨迹（思考链），格式为 `[问题，推理，答案]`。然后使用拒绝采样（reject sampling）过滤低质量或不一致的轨迹，最终保留约 9k 条高质量样本。

  2. **第一阶段：监督微调（SFT）**：使用上述推理数据对 MLLM 进行微调，使其学习“先推理、后回答”的范式，输出格式为 `<think>推理过程</think><answer>答案</answer>`。这初步将推理能力从 LLM 迁移到 MLLM。

  3. **第二阶段：强化学习（GRPO）**：基于组相对策略优化（Group Relative Policy Optimization, GRPO）进一步优化推理能力。对每个问题生成一组候选响应，计算相对优势（advantage）并更新策略，鼓励模型选择更优的推理路径。奖励包括格式奖励（强制使用`<think>`和`<answer>`标签）和准确率奖励（答案是否匹配真实标签）。KL 散度项用于保持训练稳定性。

- **公式/算法流程（文字说明）**：

  - 优化目标：最大化期望优势，同时约束更新策略与参考策略的 KL 散度。
  - 优势计算：对每组响应，`Ai = (ri - mean) / std`，实现组内归一化。
  - 训练流程：生成组响应 → 计算奖励 → 计算相对优势 → 策略梯度更新。

### 三、实验设计

- **使用的数据集**：
  - 表格问答（TQA）：TABMWP、WTQ、HiTab、TAT-QA（由于 FeTaQA 采用 BLEU 评分，不适用于准确率评估，故排除）。
  - 表格事实验证（TFV）：TabFact、InfoTabs。
  - 额外泛化测试：MMMU（仅表格相关问题，共 165 题）。
  - 训练集：从 TABMWP、WTQ、TAT-QA、TabFact、InfoTabs 中随机抽取各 2000 条，共 10000 条，拒绝采样后保留约 9000 条。

- **Benchmark 对比方法**：列举了多个开源 MLLMs 及表格理解专用模型：
  - Qwen2.5-VL-7B、InternVL-2.5-8B、MiniCPM-V-2.6-8B、Ovis2-8B、Table-LLaVA-7B、TabPedia-7B、HIPPO-8B（含 HIPPO 有无结构化表格输入的变体）。此外还对比了 DeepSeek-R1、QvQ 等大模型。

- **评估指标**：TQA 任务使用准确率（Accuracy），TFV 使用二分类/多分类准确率。采用 Qwen2.5-72B-Instruct 作为外部评估器，将评估转换为纯文本形式以减少歧义。

### 四、资源与算力

- **明确提及的算力**：
  - SFT 阶段：4 张 A100-80G GPU，训练约 1 小时。
  - RL 阶段：8 张 A100-80G GPU，训练约 24 小时。
  - 超参数：SFT 学习率 2e-6，RL 学习率 5e-7，batch size 均为 128，RL 阶段对每个问题生成 16 个候选响应。
  - 精度：bf16，启用梯度检查点。

### 五、实验数量与充分性

- **实验数量**：主实验包含 7 个数据集（TQA 4 个、TFV 2 个、MMMU 1 个），对比 8+ 种方法。此外还进行了：
  - 消融实验（图 4）：基线 vs. 仅 SFT vs. 仅 RL vs. 完整 TURBO。
  - 与推理大模型对比（表 4）：DeepSeek-R1（671B）、QvQ（72B）等。
  - 扩展性实验（表 5）：将 TURBO 框架应用于 Qwen2.5-VL。
  - 推理效率分析（表 6）。
  - 案例研究（图 5、图 6）。

- **充分性与公平性**：实验中详细说明了数据采样策略、训练/测试集不重叠、外部评估器使用、与 HIPPO 公平对比（相同 10k 采样策略）。实验覆盖了多种表格推理场景（数学、财务、多级表格等），并做了泛化测试（MMMU）。消融实验清晰展示了各组件贡献。整体实验设计较充分、客观、公平。

### 六、论文的主要结论与发现

1. **TURBO 显著提升性能**：在 7 个基准上平均准确率 76.42%，超越现有 SOTA（HIPPO 等）平均 7.2% 以上。
2. **特权结构化信息的有效性**：训练阶段利用结构化表格作为监督，即使在测试时仅提供图像，模型也能获取更强的推理能力。
3. **两阶段训练互补**：SFT 引入推理范式，RL 进一步优化推理路径，二者结合效果最佳。
4. **参数效率优异**：8B 的 TURBO 在表格图像推理上接近甚至超过 671B 的 DeepSeek-R1（在 InfoTabs 上超越），验证了框架的蒸馏能力。
5. **泛化能力强**：在未见过的 MMMU 数据集上同样取得大幅提升。
6. **可解释性提升**：模型输出显式推理链，便于调试和可信度评估。

### 七、优点

- **方法创新**：首次将“学习使用特权信息”应用于多模态表格推理，提出桥接信息（推理轨迹）来弥合模态差异。
- **数据高效**：仅用 9k 精心构造的推理数据即实现 SOTA，说明数据质量优于数量。
- **两阶段训练设计合理**：SFT 奠定基础，RL 强化贪婪和探索，利用了组相对优势无批评网络，计算开销低。
- **实验全面**：涵盖多数据集、多基线、消融、泛化、效率分析，对比公平。
- **开源友好**：基于主流开源模型 Ovis2 和 Qwen2.5-VL，易复现。

### 八、不足与局限

- **失败案例分析**：仍存在 OCR 错误（如数字误读）和复杂算术/逻辑推理错误，说明感知和精确计算能力仍有提升空间。
- **数据覆盖**：主要处理较规整的表格，对于复杂布局（合并单元格、嵌套表头等）处理能力未系统分析（HiTab 因格式问题被排除出训练集）。
- **推理速度**：由于生成长推理链，单样本推理时间约 2.7 秒（约原始 Ovis2 的 3.4 倍），但相比其他推理大模型（如 QvQ 108秒）仍较优。
- **仅在训练时使用特权信息**：未探索在测试时同时利用表格图像和结构化数据（若可用）的场景，可能限制应用范围。
- **参数量限制**：基于 7B-8B 模型，与超大模型（671B）仍有差距，部分任务（如 WTQ）落后于 DeepSeek-R1（67.80% vs 85.03%）。
- **未做统计显著性测试**：未报告 error bars 或置信区间。

（完）
