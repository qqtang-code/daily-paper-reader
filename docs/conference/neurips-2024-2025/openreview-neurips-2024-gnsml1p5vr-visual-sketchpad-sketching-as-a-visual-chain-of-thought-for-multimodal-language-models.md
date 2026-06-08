---
title: "Visual Sketchpad: Sketching as a Visual Chain of Thought for Multimodal Language Models"
title_zh: Visual Sketchpad：作为多模态语言模型视觉思维链的草图绘制
authors: "Yushi Hu, Weijia Shi, Xingyu Fu, Dan Roth, Mari Ostendorf, Luke Zettlemoyer, Noah A. Smith, Ranjay Krishna"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=GNSMl1P5VR"
tags: ["query:mm-cot"]
score: 9.0
evidence: 视觉草图画板作为多模态逐步推理的思维链
tldr: 人类通过绘图辅助推理（如几何辅助线、标记地图），但当前多模态语言模型缺少这种视觉中间步骤。本文提出Sketchpad框架，为模型提供画板和绘图工具，使其能通过绘制图形（线条、框等）进行多步规划与推理。与使用文生图模型不同，Sketchpad让模型直接绘制，更灵活。实验证明该框架在几何推理等任务上显著提升性能。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-gnsml1p5vr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 1008, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gnsml1p5vr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1440, \"height\": 686, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gnsml1p5vr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1369, \"height\": 682, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gnsml1p5vr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 705, \"height\": 522, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gnsml1p5vr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1458, \"height\": 727, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gnsml1p5vr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1163, \"height\": 777, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gnsml1p5vr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1160, \"height\": 771, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gnsml1p5vr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 661, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gnsml1p5vr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 661, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gnsml1p5vr/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 660, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gnsml1p5vr/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 659, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gnsml1p5vr/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 659, \"height\": 441, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-gnsml1p5vr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 621, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-gnsml1p5vr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1428, \"height\": 679, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-gnsml1p5vr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 686, \"height\": 480, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-gnsml1p5vr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1010, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-gnsml1p5vr/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1475, \"height\": 841, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-gnsml1p5vr/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 798, \"height\": 309, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-gnsml1p5vr/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1015, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-gnsml1p5vr/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1145, \"height\": 493, \"label\": \"Table\"}]"
motivation: 当前多模态模型缺乏绘图辅助多步推理的能力，文本CoT不足以充分利用视觉工作记忆。
method: 为多模态语言模型提供视觉草图画板和绘图工具，模型通过绘制视觉元素进行中间推理。
result: 在多个视觉推理任务上超越基线，展示了视觉CoT的有效性。
conclusion: 开创了视觉中间推理的新范式，为多模态推理提供了新的思路。
---

## Abstract
Humans draw to facilitate reasoning: we draw auxiliary lines when solving geometry problems; we mark and circle when reasoning on maps; we use sketches to amplify our ideas and relieve our limited-capacity working memory. However, such actions are missing in current multimodal language models (LMs). Current chain-of-thought and tool-use paradigms only use text as intermediate reasoning steps. In this work, we introduce Sketchpad, a framework that gives multimodal LMs a visual sketchpad and tools to draw on the sketchpad. The LM conducts planning and reasoning according to the visual artifacts it has drawn. Different from prior work, which uses text-to-image models to enable LMs to draw, Sketchpad enables LMs to draw with lines, boxes, marks, etc., which is closer to human sketching and better facilitates reasoning. \name can also use specialist vision models during the sketching process (e.g., draw bounding boxes with object detection models, draw masks with segmentation models), to further enhance visual perception and reasoning. We experiment on a wide range of math tasks (including geometry, functions, graph, chess) and complex visual reasoning tasks. Sketchpad substantially improves performance on all tasks over strong base models with no sketching, yielding an average gain of 12.7% on math tasks, and 8.6% on vision tasks. GPT-4o with Sketchpad sets a new state of the art on all tasks, including V*Bench (80.3%), BLINK spatial reasoning (83.9%), and visual correspondence (80.8%). We will release all code and data.

---

## 论文详细总结（自动生成）

# Visual Sketchpad：作为多模态语言模型视觉思维链的草图绘制

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：人类在推理时常通过绘图辅助（如几何辅助线、地图标记、草图），但当前多模态语言模型（Multimodal LMs）缺乏这种视觉中间推理步骤。现有的链式思考（Chain-of-Thought）和工具使用范式仅使用文本作为中间推理步骤，无法充分利用视觉工作记忆。
- **研究背景**：多模态语言模型（如GPT-4V、Gemini等）在图像理解、数学推理等任务中已取得进展，但在需要空间关系、细节感知和逐步可视化推理的任务中仍存在明显不足。已有工作（如SoM、Visprog）尝试通过视觉提示或工具组合来增强模型，但要么是静态的视觉提示（SoM），要么是预设代码执行（Visprog），缺乏根据中间视觉结果动态调整规划的能力。
- **整体含义**：本文提出一种新的推理范式——**视觉草图画板（Visual Sketchpad）**，赋予多模态语言模型生成和观察中间视觉草图的能力，使其像人类一样通过绘图辅助推理，从而提升在数学和视觉任务上的性能。这项工作弥合了文本推理与视觉推理之间的鸿沟，推动了更具人类智能的多模态推理。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- 将多模态语言模型视为一个**智能体（Agent）**，能够迭代地生成**思考（Thought）**、执行**动作（Action）**（即通过代码生成视觉草图），并观察**结果（Observation）**（即草图图像），最终根据积累的多模态上下文回答查询。
- 与传统的文本CoT不同，Sketchpad的中间步骤包含**视觉表征**（如绘制的线条、边界框、深度图、分割掩码等），这些视觉产物为后续推理提供直观、高效的信息。

### 关键技术细节
- **程序生成**：模型通过生成Python代码来调用绘图工具或专业视觉模型。代码框架基于AutoGen，不需要微调，直接通过提示（prompt）提供工具的函数签名和文档字符串。
- **模块组成**：
  - **数学任务模块**：使用`matplotlib`（绘制函数、辅助线）、`networkx`（绘制图结构）、`chess`库（绘制棋盘）等标准Python包。
  - **视觉任务模块**：
    - **目标检测**：基于Grounding-DINO，返回带有编号边界框的图像。
    - **分割与标记**：基于SegmentAnything和Semantic-SAM，生成彩色掩码和编号标签（类似SoM）。
    - **深度估计**：基于DepthAnything，生成深度图（Inferno颜色图，暖色表示近）。
    - **滑动窗口搜索**：用于检测小物体，将图像分割成16个窗口，返回可能包含目标的裁剪图像。
    - **图像操作**：缩放/裁剪（zoom_in_image_by_bbox）、图像叠加（overlay_images）等。
- **迭代推理流程**（如图2所示）：
  1. **Thought**：模型分析当前上下文（包括查询、之前的思考、动作和观察），生成下一步计划。
  2. **Action**：执行Python代码生成视觉草图（如绘制辅助线、调用深度估计等），并将新图像通过`display`函数返回。
  3. **Observation**：环境返回新的图像（草图），更新上下文，模型继续推理直到决定终止并给出答案。

## 3. 实验设计

### 数据集
- **数学任务**：来自IsoBench基准，共4类：
  - **几何（Geometry）**：来自Geometry3K，需根据几何图求解角度等。
  - **数学函数（Math Function）**：包括**奇偶性分类**（even/odd/neither）和**凸性分类**（convex/concave）。
  - **图算法（Graph Algorithm）**：包括**图连通性**、**最大流**、**图同构**。
  - **游戏策略（Game Strategy）**：国际象棋**胜方识别**（Winner ID），给定FEN字符串判断白胜、黑胜或平局。
- **视觉任务**：来自多个基准，共7类：
  - **V*Bench**（257个样本，小物体搜索）
  - **MMVP**（300个样本，CLIP模型的视觉短板）
  - **BLINK**：包括**相对深度**（124）、**空间推理**（143）、**拼图**（150，多图）、**视觉对应**（172，多图）、**语义对应**（139，多图）

### 对比方法
- **基线模型**：不带Sketchpad的GPT-4 Turbo、GPT-4o；其他闭源模型（Gemini-Pro、Claude 3 OPUS）；开源模型（LLaMA-2 70B、Mixtral 8x7B、LLaVA 1.5、LLaVA-NeXT）。
- **其他增强框架**：SoM（仅视觉提示）、SoM + orig.（原始图像+SoM图像）、Visprog（视觉程序合成，替换为相同GPT-4模型）。
- **Oracle Sketchpad**：使用GPT-4o+Sketchpad生成的中间视觉产物作为输入，测试开源LLaVA模型。

### 主要结果
- **数学任务（Table 1）**：Sketchpad在全部任务上带来显著提升。GPT-4o平均提升11.2%，GPT-4 Turbo平均提升23.4%。最大增益出现在最大流（+41.3%）、图同构（+14.5%）、凸性（+10.3%）。
- **视觉任务（Table 2）**：GPT-4o + Sketchpad在所有7个任务上达到新SOTA。V*Bench提升14.3%（66%→80.3%），深度提升12.1%（71.8%→83.9%），语义对应提升9.7%（48.6%→58.3%）。GPT-4 Turbo也有类似提升。
- **与SoM、Visprog比较（Table 3）**：Sketchpad是唯一在所有单图像任务上取得一致提升的框架。SoM有时会损害性能，Visprog则全面下降。
- **开源模型实验（Table 4）**：使用oracle sketchpad（即GPT-4o生成的视觉产物）输入给LLaVA-NeXT，在数学任务上也带来提升，表明视觉草图可迁移。

## 4. 资源与算力

- 论文未明确说明使用的GPU型号、数量或训练时长，因为Sketchpad本身不需要额外训练，仅使用闭源API模型（GPT-4 Turbo和GPT-4o）进行推理。
- 在附录E（Table 7）中提供了每样本的Token消耗和GPT-4o的成本估算：例如，V*Bench每样本约26,647 token，成本$0.133；数学任务每样本约2,200-3,200 token，成本$0.011-$0.016。这主要是API调用成本，未涉及训练硬件。

## 5. 实验数量与充分性

- **实验数量**：覆盖11个不同数据集/任务（数学4类+视觉7类），每个任务均对比了多个基线（至少6-8个模型），并进行了消融（与SoM、Visprog、Oracle Sketchpad对比）。
- **充分性**：
  - 任务类型多样，包括单图和多图任务、纯文本输入（如函数表达式）和图像输入。
  - 对比了主流闭源和开源模型，以及不同增强框架，公平性较好（Visprog和SoM均使用相同LM骨干）。
  - 进行了人类评估（第6节）：在几何任务上，人类与GPT-4o绘制相同辅助线的匹配率达80%；在视觉任务上，人类评定GPT-4o的计划有效率达92.8%。
  - 分析了视觉模块使用频率（Figure 4），说明工具选择与任务相关且模型间有差异。
  - 讨论了失败原因：主要源于视觉专业模型的错误或简单VQA错误，而非规划失误。
- **客观性**：结果表格清晰，增益显著，且指出了某些任务上提升较小（如MMVP+1.0%），说明没有刻意夸大。

## 6. 主要结论与发现

1. **视觉草图作为中间推理步骤能显著提升多模态语言模型的性能**，在数学和视觉任务上平均提升超过10%。
2. **Sketchpad优于现有增强框架**（SoM、Visprog），因为其允许模型根据中间视觉结果动态调整规划，具有更强鲁棒性。
3. **视觉专业模型**（如检测、分割、深度估计）可被有效集成到推理过程中，模型能灵活调用并利用其输出。
4. **模型规划与人类规划高度一致**，表明框架符合人类直觉。
5. **视觉草图对开源模型也有帮助**（通过Oracle Sketchpad实验）。

## 7. 优点

- **创新性**：首次系统性地将“人类通过绘图辅助推理”这一行为赋予多模态语言模型，提出视觉思维链（Visual CoT）概念。
- **通用性**：框架可应用于广泛的数学和视觉任务，既有纯文本输入也有图像输入，且无需微调，即插即用。
- **可解释性**：中间视觉步骤使得推理过程更透明，便于人类理解和调试。
- **模块化设计**：允许自由替换或添加视觉专业模型，具有良好的扩展性。
- **实验严谨**：多任务、多基线、人类评估、工具使用统计等多角度验证有效性。

## 8. 不足与局限

- **计算成本高**：由于需要生成并执行Python代码、调用视觉模型和API，相比直接文本推理消耗更多Token和延迟（Table 7）。
- **依赖闭源模型**：主要实验基于GPT-4 Turbo/4o，这些模型的能力边界可能影响结果；开源模型实验仅使用了Oracle Sketchpad（预先生成的草图），未验证Sketchpad本身在开源模型上的表现。
- **视觉专业模型的错误传递**：如检测失败或分割不准确，会导致后续推理出错（人类评估中2.8%的无效计划即源于此）。
- **任务覆盖有限**：虽然包含11个任务，但未涉及视频、3D、机器人等更复杂的多模态场景（作者在Limitation中提及未来方向）。
- **训练方面的缺失**：当前仅使用现成模型，未探索通过训练让模型内生地学习绘图推理（如Unified-IO 2、Chameleon等原生多模态模型）。
- **可能存在偏差风险**：视觉草图可能误导模型（例如深度图颜色解释错误），但实验中未详细分析此类失败案例。

（完）
