---
title: "GoT: Unleashing Reasoning Capability of MLLM for Visual Generation and Editing"
title_zh: GoT：释放多模态大模型在视觉生成与编辑中的推理能力
authors: "Rongyao Fang, Chengqi Duan, Kun Wang, Linjiang Huang, Hao Li, Hao Tian, Shilin Yan, Weihao Yu, Xingyu Zeng, Jifeng Dai, Xihui Liu, Hongsheng Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=eCElREEUsr"
tags: ["query:mm-cot"]
score: 7.0
evidence: 生成链式思考引导多模态推理的视觉生成
tldr: 传统图文生成缺乏显式推理。提出GoT范式，让多模态大模型在图像合成前首先生成结构化的推理链（包括语义关系、坐标等），再指导后续生成，将文本到图像转化为推理引导的过程，在多模态链式推理应用中展示了创造性潜力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1395, \"height\": 1076, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1425, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1432, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1374, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1395, \"height\": 272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 707, \"height\": 838, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1261, \"height\": 328, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1096, \"height\": 1666, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 406, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 362, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 544, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 542, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 402, \"height\": 1691, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1402, \"height\": 1010, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ecelreeusr/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1424, \"height\": 216, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ecelreeusr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 571, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ecelreeusr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 949, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ecelreeusr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 873, \"height\": 188, \"label\": \"Table\"}]"
motivation: 现有图像生成方法缺少对视觉构成的显式推理。
method: 让MLLM先生成自然语言推理链，再基于推理结果驱动生成。
result: 在图像生成和编辑任务上实现了更可控且语义更准确的结果。
conclusion: GoT展示了多模态链式推理在生成领域的应用价值。
---

## Abstract
Current image generation and editing methods primarily process textual prompts as direct inputs without explicit reasoning about visual composition or operational steps. We present Generation Chain-of-Thought (GoT), a novel paradigm that empowers a Multimodal Large Language Model (MLLM) to first generate an explicit, structured reasoning chain in natural language—detailing semantic relationships, object attributes, and, crucially, precise spatial coordinates—before any image synthesis occurs. This intermediate reasoning output directly guides the subsequent visual generation or editing process. This approach transforms conventional text-to-image generation and editing into a reasoning-guided framework that analyzes semantic relationships and spatial arrangements. We define the formulation of GoT and construct large-scale GoT datasets containing over \textbf{9M} samples with detailed reasoning chains capturing semantic-spatial relationships. To leverage the advantages of GoT, we implement a unified framework that integrates Qwen2.5-VL for reasoning chain generation with an end-to-end diffusion model enhanced by our novel Semantic-Spatial Guidance Module. Experiments show our GoT framework achieves excellent performance on both generation and editing tasks, with significant improvements over baselines. Additionally, our approach enables interactive visual generation, allowing users to explicitly modify reasoning steps for precise image adjustments. GoT pioneers a new direction for reasoning-driven visual generation and editing, producing images that better align with human intent. We will release our datasets and models to facilitate future research.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义（研究动机和背景）

- **现状问题**：当前图像生成和编辑方法通常将文本提示直接映射到图像，缺乏对场景构成、空间关系和对象交互的显式推理，导致复杂指令的理解与执行能力不足。
- **研究动机**：多模态大语言模型（MLLM）已具备强大的推理能力，但尚未被有效整合到视觉生成过程中。论文希望填补这一空白，使生成过程具备类人类的空间‑语义推理能力。
- **整体目标**：提出 **Generation Chain‑of‑Thought (GoT)** 范式，将显式推理链引入视觉生成和编辑，实现更可控、更符合人类意图的合成结果。

### 2. 方法论：核心思想、关键技术细节

- **核心思想**：在图像合成之前，让 MLLM 先生成结构化的自然语言推理链（GoT），该链包含：
  - 语义描述（对象、属性、关系）
  - 精确的空间坐标（格式 `(x1,y1),(x2,y2)`，范围 [0,1000)）
- **关键技术细节**：
  1. **GoT 数据集构建**：使用 Qwen2‑VL 和 Qwen2.5 构建自动化标注流水线，生成 900 万+ 样本（含 T2I 和编辑），每个样本包含指令、推理链和对应图像。
  2. **框架架构**（端到端）：
     - **MLLM 推理引擎**：基于 Qwen2.5‑VL‑3B，生成 GoT 链的同时输出语义引导嵌入 \(G_t\)（通过 64 个可学习 token 实现）。
     - **语义‑空间引导模块 (SSGM)**：
       - 语义引导 \(G_t\)：MLLM 生成的嵌入，通过交叉注意力注入扩散模型。
       - 空间引导 \(G_s\)：从 GoT 坐标解析出彩色编码掩码，经 VAE 编码后与扩散潜变量拼接。
       - 参考图像引导 \(G_r\)：编辑任务使用源图像，T2I 使用黑图。
  3. **引导策略**：采用分类器自由引导，联合语义、空间和参考图像引导：
     \[
     \varepsilon_\theta = \varepsilon_0 + \alpha_t(\varepsilon_{t,r} - \varepsilon_r) + \alpha_s(\varepsilon_{t,s,r} - \varepsilon_{t,r}) + \alpha_r(\varepsilon_r - \varepsilon_0)
     \]
     其中 \(\alpha_t, \alpha_s, \alpha_r\) 为引导权重（T2I 中 \(\alpha_t=7.5, \alpha_s=4.0\)；编辑中 \(\alpha_t=4.0, \alpha_s=3.0, \alpha_r=1.5\)）。
- **训练流程**：两阶段 – 预训练（60,000 步）→ 微调（10,000 步），联合优化 MLLM 的交叉熵损失和扩散模型的 MSE 损失（权重 1:1），MLLM 仅使用 LoRA 微调。

### 3. 实验设计

- **数据集**：
  - T2I：LAHR（3.77M）、JourneyDB（4.09M）、FLUX 生成（600K）。
  - 编辑：OmniEdit（736,691 样本，单轮）、SEED‑Edit‑Multiturn（180,190 样本，多轮）。
- **基准测试**：
  - T2I：GenEval（评估对象、计数、颜色、位置、属性绑定等）。
  - 编辑：Emu‑Edit（CLIP‑I / CLIP‑T）、ImagenHub（GPT‑4o 评估）、Reason‑Edit（GPT‑4o 评估）。
- **对比方法**：
  - T2I：SDv1.5 / v2.1、SD‑XL、DALL‑E2、SD3、LayoutGPT、LlamaGen、Chameleon、LWM、SEED‑X、Emu3、Janus、JanusFlow 等。
  - 编辑：InstructPix2Pix、MagicBrush、MGIE、Emu‑Edit、SEED‑X、SmartEdit、CosXL‑Edit 等。
- **消融实验**：基线（无 GoT 无 SSGM）→ 加 GoT → 加 SSGM → 完整框架（含预训练），在 GenEval 和 ImagenHub 上评估。

### 4. 资源与算力

- 数据集构建消耗 **超过 3000 NVIDIA A100 GPU 天**。
- 模型训练阶段使用 Adam 优化器，批大小 128，最大学习率 1e‑4（预训练）/ 5e‑5（微调），采用 LoRA（r=32, alpha=32）。论文未明确给出单次训练的 GPU 数量和总时长。

### 5. 实验数量与充分性

- **定量实验数量**：T2I 在 GenEval 上与 13 种方法对比；编辑在 3 个基准上与 8 种方法对比；消融实验包含 4 个设置。
- **定性实验**：展示了 T2I、交互式生成、编辑的多个目视比较样例。
- **充分性评估**：实验覆盖了主要生成和编辑任务，对比方法全面，消融验证了各组件贡献。但未报告误差棒或统计显著性检验，部分结果（如 GPT‑4o 评估）可能受评分模型影响。整体公平性合理。

### 6. 主要结论与发现

- GoT 在 **GenEval 上总体得分 0.64**，超过所有对比方法，尤其在单对象、计数、颜色任务上表现突出。
- 在编辑任务上：
  - Emu‑Edit 基准：CLIP‑I 0.864，CLIP‑T 0.276，均最优；
  - ImagenHub GPT‑4o 评分 0.533（最高）；
  - Reason‑Edit 评分 0.561（仅次于特化模型 SmartEdit 0.572）。
- 消融实验确认 GoT 链、SSGM 模块及大规模预训练均显著提升性能。
- 交互式生成允许用户修改 GoT 中文本或坐标来精确控制生成内容。

### 7. 优点

- **创新范式**：首个将显式语义‑空间推理链与图像生成/编辑端到端融合的方法，弥补了 MLLM 理解能力与生成模型之间的鸿沟。
- **大规模高质量数据集**：构建了 900 万+ 含推理链的标注数据，为后续研究提供基础。
- **模块化设计**：SSGM 同时处理语义、空间和参考图引导，且双任务无需更改架构。
- **可解释性与可控性**：GoT 链透明化中间推理，支持用户交互式修改，提升实用性。
- **鲁棒性能**：在多个基准上达到领先水平，消融实验设计清晰。

### 8. 不足与局限

- **实验统计不充分**：未提供误差棒或重复实验的方差，无法评估结果稳定性。
- **算力需求巨大**：数据标注和模型训练消耗大量 GPU 资源，可能限制可重复性。
- **部署风险未讨论**：虽提及伦理框架，但未给出具体安全措施（如内容过滤、使用限制）。
- **泛化范围有限**：仅在特定数据集（LAHR、JourneyDB、OmniEdit、SEED‑Edit）上验证，未覆盖更多样化的场景（如视频、3D）。
- **评价依赖自动度量**：CLIP‑I / CLIP‑T 和 GPT‑4o 评估存在偏差，尤其是编辑任务中“过度编辑”维度可能不够敏感。
- **未开源代码与数据**：论文声明将发布，但提交时未提供，影响可复现性。

（完）
