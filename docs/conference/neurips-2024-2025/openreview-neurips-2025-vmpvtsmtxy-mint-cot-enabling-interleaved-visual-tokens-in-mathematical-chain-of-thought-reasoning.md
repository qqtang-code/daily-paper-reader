---
title: "MINT-CoT: Enabling Interleaved Visual Tokens in Mathematical Chain-of-Thought Reasoning"
title_zh: MINT-CoT：在数学链式推理中启用交织视觉标记
authors: "Xinyan Chen, Renrui Zhang, Dongzhi Jiang, Aojun Zhou, Shilin Yan, Weifeng Lin, Hongsheng Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=vMpvtSmtXY"
tags: ["query:mm-cot"]
score: 9.0
evidence: 数学CoT中交织视觉token的多模态推理
tldr: 将CoT扩展到数学多模态场景面临三大问题：依赖粗粒度图像区域、视觉编码器对数学内容感知有限、需外部修改能力。本文提出MINT-CoT，在数学CoT推理中自适应交织视觉token，使模型可直接引用图像中的具体数学符号和图形。在多个数学VQA基准上，MINT-CoT显著超越现有方法，实现了细粒度多模态数学推理。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1425, \"height\": 822, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 232, \"height\": 173, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1424, \"height\": 701, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1435, \"height\": 664, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 379, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1397, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 272, \"height\": 128, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 395, \"height\": 169, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 394, \"height\": 166, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 283, \"height\": 149, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 546, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 178, \"height\": 148, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 215, \"height\": 168, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 529, \"height\": 125, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vmpvtsmtxy/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 277, \"height\": 158, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-vmpvtsmtxy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1453, \"height\": 834, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vmpvtsmtxy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 715, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vmpvtsmtxy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 713, \"height\": 354, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vmpvtsmtxy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1309, \"height\": 287, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vmpvtsmtxy/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1046, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vmpvtsmtxy/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1259, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vmpvtsmtxy/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1162, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vmpvtsmtxy/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 712, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vmpvtsmtxy/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 711, \"height\": 268, \"label\": \"Table\"}]"
motivation: 现有方法在数学多模态CoT中面临粗粒度图像区域和视觉编码器不足的问题。
method: 提出MINT-CoT，在数学CoT过程中动态选择并嵌入相关视觉token，与文本推理步骤交织。
result: "在MathVQA和Geometry数据集上，MINT-CoT准确率提升15%以上，且推理链更可解释。"
conclusion: 精细的视觉token交织是提升多模态数学推理性能的有效方向。
---

## Abstract
Chain-of-Thought (CoT) has widely enhanced mathematical reasoning in Large Language Models (LLMs), but it still remains challenging for extending it to multimodal domains. Existing works either adopt a similar textual reasoning for image input, or seek to interleave visual signals into mathematical CoT. However, they face three key limitations for math problem-solving: *reliance on coarse-grained box-shaped image regions, limited perception of vision encoders on math content, and dependence on external capabilities for visual modification*.  In this paper, we propose **MINT-CoT**, introducing **M**athematical **IN**terleaved **T**okens for **C**hain-**o**f-**T**hought visual reasoning. MINT-CoT adaptively interleaves relevant visual tokens into textual reasoning steps via an Interleave Token, which dynamically selects visual regions of any shapes within math figures. To empower this capability, we construct the MINT-CoT dataset, containing 54K mathematical problems aligning each reasoning step with visual regions at the token level, accompanied by a rigorous data generation pipeline. We further present a three-stage MINT-CoT training strategy, progressively combining text-only CoT SFT, interleaved CoT SFT, and interleaved CoT RL, which derives our MINT-CoT-7B model. Extensive experiments demonstrate the effectiveness of our method for effective visual interleaved reasoning in mathematical domains, where MINT-CoT-7B outperforms the baseline model by +34.08% on MathVista and +28.78% on GeoQA, respectively.

---

## 论文详细总结（自动生成）

# 论文中文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题背景**：Chain-of-Thought（CoT）在纯文本大语言模型中显著增强了数学推理能力，但将其扩展到多模态领域（同时处理图像和文本的数学问题）仍面临困难。
- **现有方法局限**：当前多模态CoT方法主要分为两类：一是仅生成纯文本推理步骤，忽略图像细节；二是尝试在推理过程中交织视觉内容（如通过边界框裁剪、注意力选择等）。但这些方法在数学场景中存在三大关键缺陷：
  1. **依赖粗粒度的框形图像区域**：如Visual-CoT、Visual SKETCHPAD等均基于边界框裁剪，但数学图像中视觉元素高度互联（如角度、线段），框选容易引入无关或误导的视觉token，损害推理准确性。
  2. **视觉编码器对数学内容感知有限**：主流编码器（CLIP/SigLIP）基于自然图像预训练，对数学图表（如几何图形、公式）属于分布外数据，难以准确定位相关区域。
  3. **依赖外部能力进行视觉修改**：一些方法（如MVoT、Visual SKETCHPAD）需要额外训练生成模型或调用外部工具，导致计算成本高、适用范围窄。
- **本文目标**：提出一种细粒度、高效的视觉交织CoT方法，使多模态大语言模型（MLLM）在数学推理中能够**动态选择与当前推理步骤最相关的视觉token（任意形状）**，实现精确的视觉-文本对齐，从而提升数学推理性能。

## 2. 论文提出的方法论

### 2.1 核心思想
引入 **Interleave Token**（交织令牌），这是一个在每一推理步骤前由模型自动生成的特殊token。通过计算Interleave Token的隐藏状态与所有视觉token之间的相似度，选择高于指定阈值的视觉token，并**动态交织**到该步骤的文本推理之前，形成“视觉-文本”交替的推理序列。

### 2.2 关键技术细节

#### 模型框架（MINT-CoT）
- **输入**：图像 $I$ 经视觉编码器得视觉特征 $V = \{v_\tau\}^N_{\tau=1}$；数学问题经文本编码器得文本特征。
- **推理过程**：
  - 在每一步 $i$ 生成 Interleave Token，其输出隐藏状态 $h^{(i)}_{\text{post\_intlv}}$ 通过**后交织投影器** $P_{\text{post\_intlv}}$ 投影。
  - 所有视觉token的隐藏状态 $h_{\text{post\_vis}}$ 通过**后视觉投影器** $P_{\text{post\_vis}}$ 投影。
  - 计算余弦相似度并缩放：$\alpha^{(i)} = \gamma \cdot \cos( P_{\text{post\_intlv}}(h^{(i)}_{\text{post\_intlv}}), P_{\text{post\_vis}}(h_{\text{post\_vis}}) )$。
  - 选择 $\alpha^{(i)}_\tau > \theta$ 的视觉token作为 $\{v^{(i)}\}$。
  - 将 $\{v^{(i)}\}$ 插入到文本步骤 $s^{(i)}$ 之前，最终输出序列为：$\{v^{(1)}, s^{(1)}, v^{(2)}, s^{(2)}, ..., v^{(k)}, s^{(k)}\}, answer$。

#### 数据集构建（MINT-CoT数据集）
- **来源**：从 Mulberry-260K 数据集中选取数学问题，提取文本CoT推理步骤。
- **四步自动生成管道**：
  1. **网格化图像**：将原始图像划分为网格，每个网格赋予唯一索引（类似ViT的patch划分）。
  2. **OCR文本定位**：使用PaddleOCR识别图像中的文字元素，将其边界框映射到网格索引，得到“OCR文本-索引”对。
  3. **提取关键词**：对每个推理步骤，用GPT-4o提取与该步骤相关的关键词语（如“线段AB”、“角DOC”）。
  4. **对齐与标注**：将关键词与网格索引关联（通过GPT-4o），将索引插入对应步骤，形成交织CoT标注。
- **数据集规模**：54K样本，每个样本包含问题、图像、交织了网格索引的推理步骤。

#### 三阶段训练策略（MINT-CoT Training Strategy）

1. **Stage 1: Text-only CoT SFT**  
   在纯文本CoT数据上微调基础模型，使模型学会基本的CoT格式（无视觉交织）。
2. **Stage 2: Interleaved CoT SFT**  
   在带交织标注的数据上联合优化：
   - 文本交叉熵损失 $L_{CE}$（监督文本tokens）。
   - 二分类交叉熵损失 $L_{BCE}$（监督视觉token选择，以标注的索引为标签）。
   - 总损失 $L = L_{CE} + L_{BCE}$。
3. **Stage 3: Interleaved CoT RL**  
   基于GRPO（组相对策略优化）框架，无监督地进一步优化模型。对一组推理链，根据答案正确性计算奖励，同时优化文本token和视觉token选择，使模型自主探索更好的交织策略。

### 2.3 公式说明（文字）
- 推理输出：$P(\{v^{(i)}, s^{(i)}\}, answer | I, T)$
- 视觉选择：余弦相似度 + 阈值过滤
- 训练目标：$L = L_{CE} + L_{BCE}$，RL阶段为 $L_{GRPO}$

## 3. 实验设计

### 3.1 使用的数据集/场景
- **GeoQA**：几何问题问答数据集（使用Geo170K测试集，英文版）
- **MathVista-Math**：MathVista的数学子集，包含四个主要任务：
  - GEO（几何推理）
  - ALG（代数推理）
  - GPS（几何问题求解）
  - TQA（教科书问答）
- **MMStar-Math**：MMStar基准的数学能力维度

### 3.2 基准方法对比
- **闭源模型**：GPT-4o, Claude-3.5 Sonnet
- **开源通用模型**：LLaVA-OneVision-Qwen2-7B, InternVL2-8B, Qwen2.5-VL-7B-Instruct等
- **开源推理模型**：Open-R1-Multimodal, R1-VL-7B, Mulberry, MM-Eureka等
- **基线模型**：Qwen2-VL-7B-Instruct

### 3.3 评估指标
准确率（Accuracy）

## 4. 资源与算力

论文在正文实验部分**未明确说明**使用的具体GPU型号、数量及训练时长。仅附录A.4提供了一些超参数：
- 基础模型：Qwen2-VL-7B
- 训练阶段：
  - Stage 1：学习率5e-6，批次大小64，训练2个epoch
  - Stage 2：学习率1e-6，批次大小64，训练3个epoch
  - Stage 3：学习率1e-6，批次大小16，组大小G=4，训练700步
- 所有参数（除视觉编码器外）均更新。视觉编码器固定。

> 注：文中未提供更详细的算力信息（如GPU型号、数量、训练总时间等）。

## 5. 实验数量与充分性

- **主要结果**：在三个基准（MathVista-Math，GeoQA，MMStar-Math）上与基线及多个SOTA方法对比（表1-3）。
- **训练阶段消融**：对比四种配置（Baseline, +Text-only CoT SFT, +Interleaved CoT SFT, +Interleaved CoT RL），在三个基准上均验证了逐阶段提升（表4）。
- **交织方法消融**：在Interleaved CoT SFT阶段，对比“原始图像交织”、“边界框区域选择”与本文“token级选择”，表明本文方法最优（表5）。
- **投影器消融**：对比有无投影器、单层线性 vs 两层MLP（附录表7）。
- **文本-only训练对比**：对比“Text-only CoT SFT + Text-only CoT RL”与本文交织方法（附录表8）。
- **额外基准**：在MMMU-Pro数学部分上也进行了阶段消融（附录表9）。
- **定量分析**：展示了训练过程中F1分数变化曲线（图4）和质量结果（图5-11）。

**评价**：实验设计较为充分，覆盖了多个公开基准、不同消融维度（训练阶段、交织方式、投影器结构、纯文本对比），且结果客观展示了方法的有效性。实验具有可重复性。

## 6. 论文的主要结论与发现

1. **MINT-CoT显著提升数学推理性能**：
   - 相比基线Qwen2-VL-7B-Instruct，在MathVista-Math上提升+32.59%（从41.11%到73.70%），GeoQA提升+26.92%（从37.80%到64.72%），MMStar-Math提升+23.2%（从46.4%到69.6%）。
2. **三阶段训练策略有效**：每个阶段均带来增益，尤其是RL阶段进一步提升了5.92%以上。
3. **细粒度token交织优于粗粒度方法**：对比原始图像交织和边界框交织，token级选择在大多数任务上表现最好。
4. **达到SOTA**：MINT-CoT-7B在MathVista-Math上超越了所有开源模型（包括7B级和8B级），甚至超过了GPT-4o和Claude-3.5 Sonnet等闭源模型。
5. **视觉token选择准确度逐步提升**：F1分数在训练中呈上升趋势，表明模型学会了更精准地定位相关视觉区域。

## 7. 优点

- **方法论创新**：首次提出通过Interleave Token实现**动态、细粒度、任意形状**的视觉token选择，摆脱了传统边界框的限制，更适应数学图像中元素紧密耦合的特点。
- **数据集构建自动化**：设计了四步流水线，利用OCR和GPT-4o自动生成交织标注数据，降低了人工成本，可扩展性强。
- **训练策略系统化**：三阶段渐进式训练从纯文本CoT → 有监督交织CoT → 强化学习探索，逐步提升模型能力，且RL阶段不依赖人工标注，能自主优化。
- **实验全面**：在多个数学专用基准上验证，消融实验覆盖训练阶段、交织方式、投影器等关键设计，结论可靠。
- **结果显著**：在7B参数规模下达到甚至超越闭源模型，展示了方法的强大潜力。

## 8. 不足与局限

- **数据集依赖GPT-4o**：标注过程中使用GPT-4o进行关键词-网格索引对齐，虽然自动化但仍有计算成本，且可能引入数据偏差或错误。
- **未探索其他RL策略**：RL阶段仅采用GRPO及其简单扩展，文中指出“其他RL策略仍未探索”，可能存在更优方案。
- **模型规模单一**：仅基于7B模型训练，未在更大规模模型（如13B、72B）上验证方法的可扩展性和泛化性。
- **视觉编码器固定**：训练时冻结了Qwen2-VL的视觉编码器，若联合微调或使用数学专用编码器（如MAVIS所提）可能进一步提升表现。
- **基准覆盖有限**：虽然涵盖了主要的数学VQA基准，但未在更多样化的多模态推理任务（如图表理解、科学问题）上评估，泛化性有待验证。
- **定量分析仅基于单次运行**：未报告多次实验的均值与方差，缺少统计显著性检验，可能受随机影响。

（完）
