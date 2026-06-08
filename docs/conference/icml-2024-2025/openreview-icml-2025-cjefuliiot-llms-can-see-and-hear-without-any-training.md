---
title: LLMs can see and hear without any training
title_zh: 无需训练，大语言模型也能看和听
authors: "Kumar Ashutosh, Yossi Gandelsman, Xinlei Chen, Ishan Misra, Rohit Girdhar"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=cJeFULIiot"
tags: ["query:mm-cot"]
score: 9.0
evidence: 免训练多模态迭代推理
tldr: 现有方法需要为每个任务训练专用模型，成本高昂。本文提出MILS，一种免训练方法，利用大语言模型本身的多步推理能力，通过迭代生成并打分候选输出，无需任何训练即可实现零样本图像、视频和音频字幕生成，还适用于媒体生成和提示重写。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1766, \"height\": 751, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 848, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 857, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 838, \"height\": 254, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 855, \"height\": 636, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 851, \"height\": 528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 839, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1767, \"height\": 511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 847, \"height\": 265, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 516, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1750, \"height\": 823, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 799, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 802, \"height\": 885, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1760, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cjefuliiot/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 854, \"height\": 525, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-cjefuliiot/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 861, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cjefuliiot/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 154, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cjefuliiot/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 139, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cjefuliiot/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 853, \"height\": 754, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cjefuliiot/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 892, \"height\": 276, \"label\": \"Table\"}]"
motivation: 多模态任务通常需要训练专用模型，缺乏零样本通用能力。
method: MILS利用LLM的多步推理能力，迭代生成候选输出并反馈打分。
result: 在图像、视频、音频字幕任务上达到零样本新SOTA。
conclusion: 无需训练即可赋予LLM多模态能力，展示了多步推理的通用性。
---

## Abstract
We present MILS: Multimodal Iterative LLM Solver, a surprisingly simple, training-free approach, to imbue multimodal capabilities into
your favorite LLM. Leveraging their innate ability to perform multi-step reasoning, MILS prompts the LLM to generate candidate outputs, each of which are scored and fed back iteratively, eventually generating a solution to the task. This enables various applications that typically require training specialized models on task-specific data. In particular, we establish a new state-of-the-art on emergent zero-shot image, video and audio captioning. MILS seamlessly applies to media generation as well, discovering prompt rewrites to improve text-to-image generation, and even edit prompts for style transfer! Finally, being a gradient-free optimization approach, MILS can invert multimodal embeddings into text, enabling applications like cross-modal arithmetic.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与研究动机
- **研究背景**：多模态任务（如图像/视频/音频字幕、文本生成图像、风格迁移等）通常需要针对每个任务训练专门的模型，依赖大量配对数据和昂贵的训练过程。即使已有零样本方法，也多限于特定模态或任务。
- **核心问题**：能否在不进行任何任务特定训练的情况下，利用现成的大语言模型（LLM）的多步推理能力，使其“看见”和“听见”并完成多种多模态任务？
- **整体含义**：论文提出一种通用于多种模态和任务的免训练框架，展示LLM自身推理与现有多模态评分器结合即可实现强大的零样本能力，挑战了“需要专用训练”的常规思路。

## 2. 方法论：MILS（Multimodal Iterative LLM Solver）
- **核心思想**：通过迭代式的“生成-评分-反馈”循环，让LLM逐步改进候选输出，优化目标函数，无需梯度。
- **关键技术细节**：
  - **Generator**：通常为一个LLM（如Llama 3.1 8B），负责根据当前候选集和评分反馈生成新的候选输出（文本形式的描述、改写后的提示等）。
  - **Scorer**：一个现成的多模态模型（如SigLIP、ViCLIP、ImageBind、PickScore、Gram Matrix等），计算生成结果与测试样本之间的相似度或质量分数。
  - **优化过程**：
    1. 初始化：可选的初始候选集（如30K多样化caption）。
    2. 循环N步（通常10-20步）：
       - Generator接收前一轮top-K候选及其分数（文本格式化），生成新一轮候选。
       - Scorer对所有候选打分，保留top-K并格式化反馈给Generator。
    3. 输出最终最优候选。
  - **特点**：梯度无关，可灵活替换Generator和Scorer以适配新任务/模态。
- **算法流程（文字说明）**：输入测试样本 -> Generator生成候选 -> Scorer评分 -> 反馈至Generator -> 迭代更新 -> 达到收敛或固定步数 -> 输出最优解。

## 3. 实验设计
- **数据集与场景**：
  - **图像字幕**：MSCOCO Karpathy test（5000张图像）。
  - **视频字幕**：MSR-VTT test（2990个视频）。
  - **音频字幕**：Clotho（音频字幕数据集）。
  - **高质量图像生成**：DrawBench（200个文本提示），使用FLUX.1[schnell]和Latent Diffusion Model作为基础T2I模型。
  - **风格迁移**：使用Emu Edit作为图像编辑模型，自定义风格/内容图像。
  - **跨模态算术**：结合图像和音频描述，通过LLM合并后生成图像。
- **基准（Benchmark）**：针对各任务的标准评估指标（BLEU-4、CIDEr、METEOR、SPICE；人类评估（质量与文本忠实度））。
- **对比方法**：
  - 图像字幕：ZeroCap、ConZIC、CLIPRe、MeaCap。
  - 视频字幕：Nagrani et al.（使用HowTo100M或VideoCC3M训练）。
  - 音频字幕：ZerAuCap。
  - 图像生成：与原始FLUX/LDM对比人类偏好。
  - 风格迁移：无定量对比，仅定性示例。
  - 跨模态算术：无直接对比，展示潜力。

## 4. 资源与算力
- **文中未明确说明使用的GPU型号、数量或训练时长**（因为MILS是免训练方法，仅有推理计算）。作者提及使用Llama 3.1 8B、SigLIP ViT-L/14等模型，但未报告具体推理时间或硬件配置。消融实验中提到初始候选集大小影响性能，但未提供计算成本数据。

## 5. 实验数量与充分性
- **实验数量**：覆盖4种主要任务（字幕：3模态；生成：2种T2I模型；编辑：1种；算术：定性），外加多项消融实验（步数、初始集大小、Generator/Scorer规模、不同LLM/Scorer类型）。
- **充分性评估**：
  - **客观性**：自动指标（如BLEU、CIDEr、METEOR、SPICE）和人工评估（图像生成的两轴偏好投票）相结合，减少单一指标偏差。
  - **公平性**：对比方法均为同类最先进的零样本方法，但部分基线（如视频字幕）使用了大量训练数据，MILS在多数语义指标上持平或超越，显示优势。但跨任务对比不完全（风格迁移、算术无定量对比），部分消融仅基于1000张图像子集。
  - **局限性**：人工评估仅针对200个提示，规模较小；缺乏运行时间对比；部分任务（如音频字幕）仅与一个基线对比。

## 6. 主要结论与发现
- **MILS能实现多种多模态任务的零样本能力**，包括图像/视频/音频字幕、文本到图像生成优化、风格迁移、跨模态模态算术。
- **在多个任务上达到新SOTA**（尤其语义指标METEOR/SPICE），且方法简单通用，无需任何任务特定训练数据。
- **性能随优化步数、初始候选集大小、生成器与评分器规模增加而提升**。
- **展示了LLM的多步推理能力可跨模态泛化**，通过简单迭代优化即可弥补现有多模态模型的不足。

## 7. 优点
- **免训练**：完全无需梯度更新或任务数据，利用现成模型即可运行，部署成本极低。
- **通用性**：同一框架可无缝应用于不同模态（图像、视频、音频）和不同任务（理解、生成、编辑、算术），仅需替换Generator/Scorer。
- **简单且可解释**：流程直观，迭代过程可观察候选进步；无黑箱梯度优化。
- **性能强大**：在多个零样本字幕任务上超越现有专用方法，尤其语义相关性指标。
- **梯度无关**：适用于无法求梯度的黑盒模型（如扩散模型、专有API），拓宽应用范围。

## 8. 不足与局限
- **性能受限于Generator和Scorer质量**：例如风格迁移仅基于Gram矩阵距离检测纹理，LLM描述风格能力有限；评分器噪声会导致次优收敛。
- **优化速度慢**：需要多次迭代（10-20步）生成新候选并评分，计算成本高，实时性差。
- **初始候选集依赖**：字幕任务需先由LLM生成大量候选，若初始集多样性不足则可能陷入局部最优。
- **评估不全面**：部分任务（跨模态算术、风格迁移）仅定性展示；视频字幕仅对比一个基线；音频字幕仅对比一个基线。缺少对失败案例的分析。
- **偏差风险**：LLM和Scorer本身可能带有训练数据中的偏见，MILS不引入新偏差但会继承现有偏差，且无法在推理时纠正。
- **未见对空间/3D任务的探索**：论文仅在2D视觉和音频上验证，应用范围仍有扩展空间。

（完）
