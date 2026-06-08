---
title: "Mastering Text-to-Image Diffusion: Recaptioning, Planning, and Generating with Multimodal LLMs"
title_zh: 掌握文本到图像扩散：利用多模态LLM进行重新描述、规划与生成
authors: "Ling Yang, Zhaochen Yu, Chenlin Meng, Minkai Xu, Stefano Ermon, Bin CUI"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=DgLFkAPwuZ"
tags: ["query:mm-cot"]
score: 7.0
evidence: 利用多模态LLM思维链规划文本到图像生成
tldr: 该论文提出RPG框架，利用多模态大语言模型的思维链推理能力作为全局规划器，将复杂文本到图像生成任务分解为多个子区域内的简单生成子任务。通过互补区域扩散，无需训练即可提升生成图像对多对象、多属性复杂提示的遵循能力。实验证明RPG在多种提示下均显著提升组成性。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 833, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1389, \"height\": 516, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1391, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1392, \"height\": 775, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1779, \"height\": 812, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 860, \"height\": 309, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1756, \"height\": 866, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1782, \"height\": 1009, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1742, \"height\": 1082, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 843, \"height\": 1464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 799, \"height\": 1187, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 848, \"height\": 907, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1294, \"height\": 565, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 745, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 320, \"height\": 315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 974, \"height\": 586, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 758, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 754, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 756, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1196, \"height\": 1241, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 755, \"height\": 393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1052, \"height\": 713, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-dglfkapwuz/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 758, \"height\": 394, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-dglfkapwuz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1593, \"height\": 570, \"label\": \"Table\"}]"
motivation: 现有扩散模型在处理包含多对象和复杂关系的文本提示时组合能力不足。
method: 提出RPG框架，用MLLM作为规划器通过CoT分解任务，进行子区域生成。
result: 无需训练即显著提升生成图像对复杂提示的遵循程度和组成性。
conclusion: 将多模态CoT推理引入生成规划是提升组合性的有效途径。
---

## Abstract
Diffusion models have exhibit exceptional performance in text-to-image generation and editing. However, existing methods often face challenges when handling complex text prompts that involve multiple objects with multiple attributes and relationships. In this paper, we propose a brand new training-free text-to-image generation/editing framework, namely Recaption, Plan and Generate (RPG), harnessing the powerful chain-of-thought reasoning ability of multimodal LLMs to enhance the compositionality of text-to-image diffusion models. Our approach employs the MLLM as a global planner to decompose the process of generating complex images into multiple simpler generation tasks within subregions. We propose complementary regional diffusion to enable region-wise compositional generation. Furthermore, we integrate text-guided image generation and editing within the proposed RPG in a closed-loop fashion, thereby enhancing generalization ability. Extensive experiments demonstrate our RPG outperforms state-of-the-art text-to-image models, including DALL-E 3 and SDXL, particularly in multi-category object composition and text-image semantic alignment. Notably, our RPG framework exhibits wide compatibility with various MLLM architectures and diffusion backbones. Our code is available at https://github.com/YangLing0818/RPG-DiffusionMaster

---

## 论文详细总结（自动生成）

# 论文中文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：现有的文本到图像扩散模型（如 SDXL、DALL-E 3）在处理**包含多个对象、多个属性及复杂关系**的文本提示时，组合生成能力不足。例如，提示“一个绿色双马尾女孩穿着橙色裙子坐在沙发上，左边窗下有一张凌乱的桌子，沙发右上方是一个充满活力的水族箱”时，现有模型常常出现对象遗漏、属性绑定错误、空间关系错乱等问题。
- **整体含义**：论文提出一种**无需训练**的框架 RPG（Recaption, Plan and Generate），利用**多模态大语言模型（MLLM）的思维链（CoT）推理能力**，将复杂生成任务分解为多个子区域的简单子任务，从而显著提升扩散模型的组合性与可控性。

## 2. 方法论：核心思想、关键技术细节

### 2.1 核心思想
- 利用 MLLM（如 GPT-4）作为**全局规划器**，将复杂文本提示分解为：
  - **重新描述（Recaption）**：将原始提示分解为若干子提示，并重新描述为更详细、信息更丰富的描述。
  - **思维链规划（CoT Planning）**：根据子提示，将图像空间划分为**互补的非重叠子区域**，并分配每个子提示到对应的区域。
  - **互补区域扩散（Complementary Regional Diffusion）**：在每个去噪步骤中，对每个子区域独立生成潜在表示，然后通过拼接和加权融合得到整体图像。

### 2.2 关键技术细节
1. **重新描述阶段**  
   - 使用 MLLM 从复杂提示中提取关键短语，生成子提示集 \(\{y_i\}\)，再通过文本到文本重新描述得到更详细的描述 \(\{\hat{y}_i\}\)。
2. **CoT 规划阶段**  
   - 设计**任务模板与上下文示例**，激发 MLLM 的 CoT 推理，生成区域分割方案（如“1,1,1;2,1,1”表示先按行再按列划分）。  
   - 遵循两条原则：相同类名对象分配到不同区域；重点描述某实体的外观时，将实体各部分视为不同实体。
3. **互补区域扩散**  
   - 构建提示批次：基础提示 \(y_{base}\) + 各子提示 \(\{\hat{y}_i\}\)。  
   - 在每个时间步，对每个子区域独立进行交叉注意力计算，生成潜在表示 \(z_{t-1}^i\)。  
   - 将各子区域潜在表示**调整大小并拼接**得到 \(z_{t-1}^{cat}\)，再与基础提示潜在表示 \(z_{t-1}^{base}\) 进行**加权融合**：  
     \[
     x_{t-1} = \beta \cdot z_{t-1}^{base} + (1-\beta) \cdot z_{t-1}^{cat}
     \]  
     其中 \(\beta\) 平衡图像的语义一致性与视觉效果。

### 2.3 文本引导图像编辑的扩展
- 将 RPG 扩展到编辑任务：MLLM 分析源图像与目标提示之间的**跨模态语义差异**，生成编辑计划（增加、删除、修改）。  
- 使用**轮廓掩码与修补**进行精确编辑，可进行**多轮闭环自优化**。

## 3. 实验设计

### 3.1 数据集与基准
- **定性评估**：在三种复杂场景（属性绑定、数值准确性、复杂关系）上，对比 DALL-E 3、SDXL、LMD+ 等模型。
- **定量评估**：使用 **T2I-CompBench** 基准，该基准专门用于评估组合式文本到图像生成，包含颜色、形状、纹理、空间关系、非空间关系及复杂组合等子指标。

### 3.2 对比方法
- 基线方法：Stable Diffusion v1.4/v2、Composable Diffusion、Structured Diffusion、Attn-Exct v2、GORS、DALL-E 2、SDXL、PixArt-α、ConPreDiff 等。  
- 编辑任务对比：Prompt2Prompt、InstructPix2Pix、MasaCtrl。

### 3.3 实验设置
- MLLM 使用 **GPT-4**（作为重新描述和 CoT 规划器）。  
- 扩散骨干使用 **SDXL**。  
- 无需任何训练，所有操作在推理时完成。

## 4. 资源与算力
- **论文未明确说明使用的 GPU 型号、数量或训练时长**。因为该方法为**训练无关**（training-free），仅需推理计算，所以算力需求远低于需要微调的方法。实验报告中未提供具体的推理时间或硬件配置信息。

## 5. 实验数量与充分性

### 5.1 实验数量
- **定性比较**：展示了多组不同场景的生成图像，包括属性绑定、数值准确性、复杂关系等，每种场景至少 3–5 组示例。  
- **定量比较**：在 T2I-CompBench 的 6 个指标上进行了系统对比（见表 1）。  
- **消融实验**：  
  - 重新描述效果（有无 Recaption）；  
  - CoT 规划效果（有无 CoT Planning）；  
  - 基础提示权重 \(\beta\) 的影响（不同 ratio）。  
- **泛化性实验**：  
  - 将 RPG 应用于不同 MLLM（Llama 2-13B/70B、MiniGPT-4、Vicuna）；  
  - 将 RPG 应用于不同扩散骨干（SD v2.1、ConPreDiff、ControlNet）；  
  - 层次化区域扩散（增加层次数）的效果。  
- **编辑任务**：定性比较与多轮编辑示例。

### 5.2 充分性与公平性
- **充分**：消融实验覆盖了所有关键模块，泛化性实验验证了框架的灵活性。  
- **公平**：定量比较均在公开基准 T2I-CompBench 上进行，基线结果直接引用自原始论文，对比公平。但部分基线（如 DALL-E 3）未在同一硬件上重复实验，可能存在实现细节差异。

## 6. 主要结论与发现

1. **RPG 框架在组合生成上显著优于现有方法**：无论是定性还是定量（T2I-CompBench 上所有指标第一），尤其在**属性绑定、数值准确性、复杂关系**方面提升巨大（如颜色绑定得分从 0.70→0.87）。  
2. **重新描述和 CoT 规划缺一不可**：缺少重新描述会导致细节丢失；缺少 CoT 规划会导致关系混乱。  
3. **互补区域扩散有效解决了重叠对象和布局冲突问题**：通过加权融合基础提示，实现了自然和谐的图像拼接。  
4. **框架具有高度通用性**：可适配不同 MLLM 和扩散骨干，并扩展到编辑任务，实现闭环自优化。

## 7. 优点

1. **无需训练**：直接在推理阶段增强扩散模型的组合能力，大幅降低资源需求。  
2. **利用 MLLM 的 CoT 能力**：首次将 MLLM 作为多重角色（重新描述器 + 全局规划器 + 反馈提供器），充分发挥其视觉语言先验。  
3. **互补区域扩散设计巧妙**：非重叠区域独立生成 + 加权融合，避免对象冲突，同时保持全局一致性。  
4. **统一生成与编辑**：一个框架同时支持文本到图像生成和编辑，并支持闭环迭代优化。  
5. **泛化性强**：与多种 MLLM 和扩散骨干兼容，易于扩展。

## 8. 不足与局限

1. **依赖 MLLM 输出质量**：规划结果受 GPT-4 等模型的 CoT 推理质量影响，若提示设计不佳或模型性能有限，可能导致区域划分不合理。  
2. **计算开销**：虽然无需训练，但推理时需多次调用 MLLM 进行规划，且每个时间步需为多个子区域并行计算（增加内存和时间消耗）。论文未提供具体推理时间对比。  
3. **定量基准覆盖有限**：仅在 T2I-CompBench 上进行量化评估，缺乏更广泛的主流图像质量指标（如 FID、CLIP score）。  
4. **编辑任务评估不完整**：仅展示定性结果，缺少编辑任务（如 InstructPix2Pix 基准）上的定量对比。  
5. **区域划分规则依赖人工设计**：目前的分割方案（行/列比例）需要用户或 MLLM 指定，不够自动化。  
6. **极端复杂场景可能失败**：当子区域数量过多或对象关系极其复杂时，区域拼接可能出现边界不自然（论文中未充分讨论失败案例）。

（完）
