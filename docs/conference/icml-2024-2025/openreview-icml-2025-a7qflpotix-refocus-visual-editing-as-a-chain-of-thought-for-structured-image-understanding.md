---
title: "ReFocus: Visual Editing as a Chain of Thought for Structured Image Understanding"
title_zh: "ReFocus: 将视觉编辑作为思维链用于结构化图像理解"
authors: "Xingyu Fu, Minqian Liu, Zhengyuan Yang, John Richard Corring, Yijuan Lu, Jianwei Yang, Dan Roth, Dinei Florencio, Cha Zhang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=a7qFlPOTix"
tags: ["query:mm-cot"]
score: 9.0
evidence: 将视觉编辑作为思维链用于结构化图像理解
tldr: 该论文提出ReFocus框架，让多模态大模型通过生成Python代码进行图像编辑（画框、高亮、遮罩等），将视觉编辑作为思考步骤，形成推理链以理解表格、图表等结构化图像。这种方法赋予了模型多跳选择性注意能力，实验表明在多个结构化理解任务上优于现有方法，且推理过程可解释。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1773, \"height\": 657, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1751, \"height\": 670, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1651, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1761, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 897, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 853, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1751, \"height\": 200, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1749, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 798, \"height\": 729, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 809, \"height\": 759, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 521, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 529, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 530, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-a7qflpotix/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 530, \"height\": 462, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-a7qflpotix/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1766, \"height\": 718, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-a7qflpotix/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1764, \"height\": 629, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-a7qflpotix/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 852, \"height\": 185, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-a7qflpotix/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 849, \"height\": 519, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-a7qflpotix/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1772, \"height\": 491, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-a7qflpotix/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1397, \"height\": 440, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-a7qflpotix/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1395, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-a7qflpotix/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1019, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-a7qflpotix/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1465, \"height\": 324, \"label\": \"Table\"}]"
motivation: 当前多模态模型缺乏在结构化图像（如表格、图表）中进行多跳选择性注意的能力。
method: 让模型生成Python代码调用工具修改输入图像，逐步移动视觉焦点形成推理链。
result: 在多个结构化理解基准上性能提升，且推理过程可解释。
conclusion: 将视觉操作作为思维链是提升结构化图像推理的有效范式。
---

## Abstract
Structured image understanding, such as interpreting tables and charts, requires strategically refocusing across various structures and texts within an image, forming a reasoning sequence to arrive at the final answer. However, current multimodal large language models (LLMs) lack this multihop selective attention capability. In this work, we introduce ReFocus, a simple yet effective framework that equips multimodal LLMs with the ability to generate ``visual thoughts'' by performing visual editing on the input image through code, shifting and refining their visual focuses. Specifically, ReFocus enables multimodal LLMs to generate Python codes to call tools and modify the input image, sequentially drawing boxes, highlighting sections, and masking out areas, thereby enhancing the visual reasoning process. We experiment upon a wide range of structured image understanding tasks involving tables and charts. ReFocus largely improves performance on all tasks over GPT-4o without visual editing, yielding an average gain of 11.0% on table tasks and 6.8% on chart tasks. We present an in-depth analysis of the effects of different visual edits, and reasons why ReFocus can improve the performance without introducing additional information. Further, we collect a 14k training set using ReFocus, and prove that such visual chain-of-thought with intermediate information offers a better supervision than standard VQA data, reaching a 8.0% average gain over the same model trained with QA pairs and 2.6% over CoT.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：结构化图像（如表格、图表）的理解需要多步推理和选择性注意——模型需在图像的不同结构间“重新聚焦”，逐步聚焦相关信息，忽略无关内容。然而，当前多模态大语言模型（MLLMs）缺乏这种**多跳选择性注意能力**，它们的中间推理仅限于文本格式（例如将图像转为文本后用COT推理），很少再回头审视图像，导致在复杂结构化图像任务上表现不佳。
- **核心问题**：如何让MLLMs在推理过程中主动调整视觉焦点，通过可执行的视觉操作来辅助多步推理，从而提升结构化图像理解的准确性和可解释性。
- **整体含义**：论文提出**ReFocus**框架，让模型通过Python代码调用图像编辑工具（遮罩、画框、高亮）对输入图像进行**视觉编辑**，将编辑动作作为“视觉思维链”的中间步骤，逐步移动和细化视觉焦点。这一范式将视觉推理从文本链拓展到视觉空间，显著提升了模型在表格/图表问答上的性能，且无需引入外部知识。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用MLLM（如GPT-4o）生成Python代码，调用预定义的图像编辑函数对输入图像进行修改（遮罩无关区域、画框聚焦相关区域、高亮关键行/列），修改后的图像作为下一轮推理的输入，迭代进行，直到得出最终答案。这个过程模拟了人类“先扫视整体，再聚焦局部”的视觉推理策略。
- **关键技术细节**：
  - **视觉编辑工具**：提供三类操作（遮罩mask、画框draw、高亮highlight），分别应用于表格和图表的不同粒度：
    - 表格：列/行级别的遮罩、画框、高亮。
    - 图表（水平/垂直条形图、多子图科学图表）：按x值或y值（或子图）进行操作。
  - **坐标系获取**：
    - 表格：使用OpenCV检测线条和文本框的轮廓，自动计算每列/行的边界框。
    - 图表：利用OpenCV检测子图轮廓（取top-k最长轮廓供模型选择），或使用数据集自带坐标信息（如x/y轴值坐标）。
  - **推理流程**：
    1. 输入原始图像+问题。
    2. MLLM输出“Thought”（如“需要聚焦列A和列B”）和“Action”（Python代码调用编辑函数）。
    3. 系统执行代码，生成编辑后的新图像。
    4. 将新图像作为输入，MLLM继续下一步思考，直到得出结论。
  - **模型与提示**：基于GPT-4o，通过系统提示提供工具函数签名和示例，引导模型生成代码。温度设为0以确保确定性。

### 3. 实验设计：数据集、基准、对比方法

- **数据集**：
  - **表格任务**：TableVQA基准下的三个子集：
    - VWTQ（750 QA对，源自WikiTableQuestion，Wikipedia风格表格）
    - VWTQ_syn（250 QA对，合成不同风格的表格）
    - VTabFact（250 QA对，表格事实验证任务）
  - **图表任务**：
    - CharXiv多子图（143 QA对，从arXiv论文图表中精选包含多个子图的复杂科学图表）
    - ChartQA水平条形图（444 QA对）
    - ChartQA垂直条形图（382 QA对）
- **基准方法**：
  - 基线MLLMs：LLaVA-NeXT系列（7B/13B/34B）、Phi-3 Vision、Gemini-Pro 1.5、GPT-4o（两个版本：2024-05-13/2024-08-06）——均使用CoT提示但无编辑能力。
  - 可编程视觉推理：VisProg（替换为GPT-4o，但使用文本+视觉模块）。
  - 消融对比：不同编辑工具（mask/draw/highlight）、是否编辑、不同输入形式（纯文本表格/图像/文本+图像）。
- **评估指标**：准确率（通过GPT-4判断预测是否与正确答案一致）。

### 4. 资源与算力

- **推理阶段**（开源模型）：使用4块 **NVIDIA Quadro RTX 8000 GPU**（48GB），耗时约 **40 GPU小时**。
- **微调阶段**：使用8块 **NVIDIA RTX A6000 GPU**（每块48GB），采用全参数微调，搜索学习率和epoch数。具体训练时长未明确说明。

### 5. 实验数量与充分性

- **实验数量**：论文进行了多组实验，覆盖：
  - 主实验：在6个数据集（3表格+3图表）上比较ReFocus+GPT-4o与基线（表1）。
  - 跨模型迁移实验：用ReFocus编辑后的图像输入给开源模型（表2），观察是否受益。
  - 编辑工具消融：在VWTQ和VWTQ_syn上测试单一工具类型（表3）。
  - 编辑频率统计：统计各数据集编辑图像的比例（图5）。
  - 输入对比：比较ReFocus与纯文本/文本+图像输入（表5）。
  - 微调实验：构建14k训练集，对比SFT with QA/CoT/ReFocus VCoT数据（表4）。
- **充分性与公平性**：
  - 实验中尽量控制了变量（如所有GPT-4o基线均使用相同模型版本和CoT提示）。
  - 消融实验覆盖了主要编辑类型，并分析了编辑带来的具体改进（如OCR改善、视觉定位修正）。
  - 但某些数据集样本量较小（如CharXiv仅143例），可能影响统计稳定性。

### 6. 论文的主要结论与发现

- **核心结论**：ReFocus在所有结构化图像任务上持续提升GPT-4o性能，表格平均提升11.0%，图表平均提升6.8%。
- **分析发现**：
  - 视觉编辑不引入外部信息，仅通过**选择性注意**改善视觉定位和OCR精度，减少幻觉。
  - 三种编辑工具效果相近，但遮罩在某些场景下优势略大（如表格中对无关列进行遮罩）。
  - 模型自主决定是否编辑，GPT-4o在≥85%的表格和多子图任务中选择了编辑。
- **微调发现**：使用ReFocus自动生成的14k VCoT数据对Phi-3.5-vision进行SFT，相比标准QA数据提升8.0%，相比仅含文本CoT的数据提升2.6%，表明**中间视觉注意力信息提供了更强的监督信号**。

### 7. 优点：方法或实验设计上的亮点

- **简洁有效**：仅通过简单的图像编辑操作（遮罩、画框、高亮）即可显著提升性能，无需训练复杂模块或依赖外部知识。
- **可解释性强**：编辑动作和视觉变化直观展示了模型的推理步骤，增加了透明度和可审计性。
- **适用性广**：同时覆盖表格和多种图表类型（水平/垂直条形图、多子图科学图表），且编辑工具可轻松扩展。
- **蒸馏潜力**：构建的VCoT训练数据可以用于小模型监督，展示了将大模型推理能力迁移到轻量模型的途径。
- **实验设计合理**：进行了充分的消融（编辑类型、输入形式、跨模型泛化）、统计编辑频率、分析改进原因，并与多种基线公平对比。

### 8. 不足与局限

- **依赖坐标获取**：表格和图表坐标需要依赖OpenCV或数据集提供，自动检测可能不准确，限制了在任意图像上的即插即用。
- **仅针对结构化图像**：方法主要针对文本丰富的表格/图表，未验证在自然图像或物体推理任务上的效果，推广性存疑。
- **模型依赖**：当前ReFocus基于GPT-4o（商业模型），开源模型在接收编辑图像后性能提升有限（表2），表明其本身就缺乏对编辑后图像的理解能力。
- **实验规模有限**：部分数据集（如VTabFact仅250例、CharXiv仅143例）样本量较小，结果可能受噪声影响。
- **编辑决策不确定性**：GPT-4o可能做出错误或不必要的编辑（例如在无需编辑的简单问题上仍尝试编辑），文中未详细分析失败案例占比。
- **资源开销**：多步迭代增加了推理时间（每次编辑需一次API调用），实际部署成本较高。

（完）
