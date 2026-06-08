---
title: "More Thinking, Less Seeing? Assessing Amplified Hallucination in Multimodal Reasoning Models"
title_zh: 思考越多，看到越少？评估多模态推理模型中的放大幻觉
authors: "Zhongxing Xu, Chengzhi Liu, Qingyue Wei, Juncheng Wu, James Zou, Xin Eric Wang, Yuyin Zhou, Sheng Liu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=KzU33wR875"
tags: ["query:multimodal"]
score: 7.0
evidence: 分析多模态推理模型中因长链推理导致的幻觉问题
tldr: 多模态大语言模型在测试时计算增强后生成长推理链，但同时也带来更多幻觉。论文发现长链推理降低了模型对图像的关注，导致依赖语言先验。为此提出RH-AUC指标量化推理长度与感知准确率的关系，为评估模型是否保持视觉依据提供了新工具。该研究揭示了多模态推理中准确性与幻觉之间的权衡。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1366, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1450, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1449, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1449, \"height\": 407, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1393, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1457, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1018, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1012, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1506, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1457, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1394, \"height\": 1214, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1515, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1522, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1457, \"height\": 661, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kzu33wr875/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1438, \"height\": 660, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-kzu33wr875/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1421, \"height\": 433, \"label\": \"Table\"}]"
motivation: 多模态推理模型在生成长链推理时幻觉增加，需要系统研究其机制并建立评估指标。
method: 通过注意力分析和提出RH-AUC指标，定量测量推理长度对感知准确性的影响。
result: 实验表明长链推理导致视觉注意力减少，幻觉增加，RH-AUC能有效评估模型视觉接地保持能力。
conclusion: 多模态推理模型的长链思考会带来幻觉放大，需在设计时权衡推理质量与视觉基础。
---

## Abstract
Test-time compute has empowered multimodal large language models to generate extended reasoning chains, yielding strong performance on tasks such as multimodal math reasoning. However, we observe that this improved reasoning ability often comes with increased hallucination: as generations become longer, models tend to drift away from image-grounded content and rely more on language priors. Attention analysis reveals that longer reasoning chains reduce focus on visual inputs, contributing to hallucination. To systematically study this phenomenon, we introduce RH-AUC, a metric that quantifies how a model's perception accuracy changes with reasoning length, enabling evaluation of whether the model preserves visual grounding while reasoning. We also release RH-Bench, a diagnostic benchmark covering diverse multimodal tasks, designed to jointly assess the balance of reasoning ability and hallucination. We find that (i) larger models generally exhibit a better balance between reasoning and perception; (ii) reasoning and perception balance depends more on the types and domains of the training data than its volume. Our findings highlight the need for evaluation frameworks that account for both reasoning quality and perceptual reliability.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：多模态大语言模型（MLLMs）通过测试时计算（test-time compute）生成长推理链，在数学推理等任务上取得显著提升。但作者观察到，推理能力的提升往往伴随着幻觉（hallucination）的增加：生成的推理链越长，模型越倾向于偏离图像真实内容，转而依赖语言先验（language priors）。
- **核心问题**：多模态推理模型在感知型任务（如视觉问答）中是否比非推理版本更容易产生幻觉？为什么？如何系统评估推理深度与幻觉风险之间的平衡？
- **整体含义**：揭示了多模态推理中“更强推理能力可能以牺牲视觉接地为代价”的权衡，呼吁评估框架应同时考虑推理质量和感知可靠性。

## 2. 论文提出的方法论：核心思想、关键技术细节
### 核心思想
- 多模态推理模型在长链推理中会降低对视觉token的注意力分配，从而放大幻觉。作者提出用**RH-AUC**（Reasoning-Hallucination Area Under Curve）指标量化推理长度与感知准确率之间的动态平衡，并构建**RH-Bench**诊断基准来联合评估推理能力与幻觉风险。

### 关键技术细节
- **注意力分析**：对比推理模型与非推理模型的跨层注意力分布，发现推理模型对视觉token的注意力显著降低，且随推理链增长进一步减弱。
- **推理长度控制策略**：
  - Token Budget Forcing：硬性限制推理token预算。
  - Test Time Scaling：通过插入“Wait”标记软性延长推理。
  - Latent State Steering：从长/短推理轨迹的隐藏状态差异中提取方向向量，通过缩放因子α动态调整推理长度（α∈[-0.15, 0.15]）。
- **RH-AUC公式**：对每个推理长度T计算推理性能R_T和幻觉性能H_T，对(R_T, H_T)曲线使用梯形法则计算面积，并进行min-max归一化，公式为：
  ```
  RH-AUC = Σ_{i=0}^{n-2} [ (R_{T(i+1)} - R_{T(i)}) / 2 * (H_{T(i+1)} + H_{T(i)}) ]
  ```
  值越高表示在不同推理长度下推理和幻觉的平衡越好。

## 3. 实验设计：数据集、benchmark、对比方法
- **数据集**：
  - 幻觉基准：MMVP, MMEval-Pro, VMCBench, Bingo, MMHAL-Bench。
  - 推理与感知联合诊断：**RH-Bench**（1000个样本，分为推理任务500个来自MathVision, MathVista, MMMU, ScienceQA；感知任务500个来自MMhalu, MMVP, HallusionBench, VMCBench；每种包含多项选择和开放问题）。
- **对比方法**：
  - 基础非推理模型：Qwen2.5-VL-3B, Qwen2.5-VL-7B。
  - 推理模型（共8个）：LMM-R1, MM-R1, ThinkLite-VL, MM-Eureka, Ocean-R1（RL-only）；Vision-R1, R1-OneVision, OpenVLThinker, Curr-ReFT（SFT+RL）。
  - 均基于Qwen2.5-VL骨干网络。

## 4. 资源与算力
- 论文未明确说明使用的GPU型号、数量或训练时长。但提到模型相关训练细节来自各原始论文，未进行重新训练。推理实验可能使用标准GPU（如A100或类似），但具体信息缺失。

## 5. 实验数量与充分性
- **实验数量**：
  - 幻觉比较实验：在5个幻觉数据集上对比8个推理模型与2个基础模型。
  - 训练范式分析：比较RL-only、SFT+RL与基础模型在4个感知基准上的表现。
  - 注意力分析：多个层级的注意力分布可视化与热力图。
  - 推理长度控制实验：使用3种策略在5个推理模型上，对6个基准（推理+感知）进行调节，每个策略生成多组长度数据。
  - RH-Bench评估：在RH-Bench上运行所有模型，输出RH-AUC及任务准确率。
  - 消融实验：对比不同训练数据量、训练范式、模型规模的影响。
- **充分性与公平性**：
  - 实验覆盖多种数据集和任务类型，涵盖感知和推理。
  - 对比了多种流行推理模型，控制了骨干网络（Qwen2.5-VL）和规模（3B, 7B）。
  - 采用了多种推理长度控制策略，避免单一方法的偏差。
  - 但所有推理模型均基于同一骨干，可能限制泛化性。论文也承认未进行受控重训练实验，结论为观测性而非因果性。

## 6. 论文的主要结论与发现
- **发现1**：多模态推理模型在感知任务中一致地比非推理模型产生更多幻觉，且此现象在3B和7B尺度上均成立。
- **发现2**：推理长度对性能有非单调影响：适度推理长度效果最佳，过短或过长都会降低准确率；最优长度因任务而异（如数学推理需更长，感知任务需更短）。
- **发现3**：RL-only训练比SFT+RL获得更好的推理-幻觉平衡，因为RL促进更自适应、更简洁的推理，而SFT可能引入僵化的模仿路径。
- **发现4**：更大模型（7B vs 3B）通常表现出更好的平衡和稳定性。
- **发现5**：训练数据的类型和领域（如数学数据）比数据量更能影响推理-幻觉平衡。

## 7. 优点
- **问题新颖**：首次系统研究多模态推理模型中的幻觉放大现象，揭示了长链推理与视觉接地之间的权衡。
- **方法论创新**：提出RH-AUC指标量化动态平衡，克服了传统单点指标的局限性；Latent State Steering方法为精确控制推理长度提供了新工具。
- **基准贡献**：发布RH-Bench诊断数据集，专门用于联合评估推理与感知，推动未来研究。
- **实验设计严谨**：多种控制策略、多模型、多数据集、多尺度对比，结论具有较强稳健性。
- **可解释性**：通过注意力分析和案例研究揭示了幻觉产生的内在机制（视觉注意力下降）。

## 8. 不足与局限
- **通用性受限**：所有评估模型基于Qwen2.5-VL骨干，未覆盖其他架构（如LLaVA、InternVL等），结论可能不具完全普适性。
- **缺乏因果验证**：对训练数据影响的分析仅基于技术报告，未进行受控重训练实验，结论为观测性。
- **推理控制策略局限**：Token Budget Forcing和Test Time Scaling对长度的调节不够精细，而Latent State Steering需要构建长短轨迹，可能依赖特定数据。
- **计算资源未报告**：未说明GPU型号、数量、训练/推理时间，影响可复现性。
- **任务覆盖有限**：RH-Bench虽涵盖多样任务，但主要涉及自然图像，未涉及视频、多图、语音等多模态场景。
- **潜在偏差**：开放问题评估使用GPT-4o，可能引入评判者偏差；评分标准可能不够全面。

（完）
