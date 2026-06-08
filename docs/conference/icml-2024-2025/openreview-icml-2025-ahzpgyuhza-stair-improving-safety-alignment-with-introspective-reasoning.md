---
title: "STAIR: Improving Safety Alignment with Introspective Reasoning"
title_zh: "STAIR: 通过内省推理提升安全对齐"
authors: "Yichi Zhang, Siyuan Zhang, Yao Huang, Zeyu Xia, Zhengwei Fang, Xiao Yang, Ranjie Duan, Dong Yan, Yinpeng Dong, Jun Zhu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=aHzPGyUhZa"
tags: ["query:mm-cot"]
score: 6.0
evidence: 利用思维链进行安全对齐
tldr: 该论文提出STAIR框架，通过自我改进的思维链推理逐步识别安全风险，将安全对齐与内省推理结合。首先赋予模型结构化推理能力，然后通过迭代偏好优化提升安全对齐。该方法在保持模型性能的同时增强了安全性，减少了安全-性能权衡和越狱攻击的脆弱性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ahzpgyuhza/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 847, \"height\": 520, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ahzpgyuhza/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1766, \"height\": 807, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ahzpgyuhza/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 520, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ahzpgyuhza/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 516, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ahzpgyuhza/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 563, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ahzpgyuhza/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1447, \"height\": 70, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ahzpgyuhza/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1438, \"height\": 98, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ahzpgyuhza/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1777, \"height\": 1081, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ahzpgyuhza/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 866, \"height\": 422, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ahzpgyuhza/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 869, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ahzpgyuhza/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 573, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ahzpgyuhza/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 863, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ahzpgyuhza/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 871, \"height\": 501, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ahzpgyuhza/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 865, \"height\": 377, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ahzpgyuhza/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1656, \"height\": 990, \"label\": \"Table\"}]"
motivation: 现有安全对齐方法存在安全-性能权衡和易受越狱攻击的问题，需改进。
method: 集成内省推理，利用自我改进的思维链逐步分析风险，并通过偏好优化对齐安全。
result: 在提升安全性的同时保持了模型性能，有效抵御越狱攻击。
conclusion: 将推理链引入安全对齐是有效途径，平衡了安全与性能。
---

## Abstract
Ensuring the safety and harmlessness of Large Language Models (LLMs) has become equally critical as their performance in applications. However, existing safety alignment methods typically suffer from safety-performance trade-offs and susceptibility to jailbreak attacks, primarily due to their reliance on direct refusals for malicious queries. In this paper, we propose **STAIR**, a novel framework that integrates **S**afe**T**y **A**lignment with **I**trospective **R**easoning. We enable LLMs to identify safety risks through step-by-step analysis by self-improving chain-of-thought (CoT) reasoning with safety awareness. STAIR first equips the model with a structured reasoning capability and then advances safety alignment via iterative preference optimization on step-level reasoning data generated using our newly proposed Safety-Informed Monte Carlo Tree Search (SI-MCTS). Specifically, we design a theoretically grounded reward for outcome evaluation to seek balance between helpfulness and safety. We further train a process reward model on this data to guide test-time searches for improved responses. Extensive experiments show that STAIR effectively mitigates harmful outputs while better preserving helpfulness, compared to instinctive alignment strategies. With test-time scaling, STAIR achieves a safety performance comparable to Claude-3.5 against popular jailbreak attacks. We have open-sourced our code, datasets and models at https://github.com/thu-ml/STAIR.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：大语言模型（LLM）的安全对齐方法（如SFT、DPO、RLHF）通常存在**安全性-有用性权衡**（trade-off）和对**越狱攻击（jailbreak）的脆弱性**。现有方法主要依赖直接拒绝（direct refusal）来应对有害查询，这种“浅层对齐”（shallow alignment）类似于系统1思维（快速、本能），一旦被越狱绕过，模型就会生成有害内容。
- **整体含义**：论文提出应将**内省推理（Introspective Reasoning）** 引入安全对齐，使模型能够通过逐步分析（类似于系统2思维）识别潜在风险，从而在保持有用性的同时提升安全性，抵抗复杂的越狱攻击。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：提出**STAIR**框架，将安全对齐与内省推理相结合，通过**三个关键阶段**实现：
  1. **结构化CoT格式对齐**：先用少量安全/有用性数据对模型进行SFT，使其输出遵循结构化的思维链格式（每个推理步骤用特殊标记包裹，最终输出用`<|Output|>`标记）。
  2. **基于Safety-Informed MCTS（SI-MCTS）的自我改进**：
     - 构建搜索树，每个推理步骤作为一个节点。使用**安全信息奖励函数**`R(H,S) = S·H + 2S`（满足三个理论属性：安全优先、双单调性、可退化到单目标），兼顾有用性（H）和安全性（S）。
     - 采用**自奖励机制**：用模型自身对最终答案进行有用性和安全性评分，避免外部标注成本。
     - 从搜索树中通过阈值采样提取**步级偏好数据**（stepwise preference pairs），使用**步级DPO**（step-level DPO）进行优化，公式为：
       ```text
       -log σ(β log (πθ(z_w|x,s_i)/πref(z_w|x,s_i)) - β log (πθ(z_l|x,s_i)/πref(z_l|x,s_i)))
       ```
     - 上述过程可迭代进行（K=3轮），每次使用前一轮模型生成更高质量的数据。
  3. **测试时扩展（Test-time Scaling）**：
     - 利用SI-MCTS搜索树中的节点价值，训练一个**过程奖励模型（Process Reward Model, PRM）**，用于评估部分推理轨迹。
     - 在推理时使用**Best-of-N**和**Beam Search**等搜索算法，生成更安全的回答。

## 3. 实验设计：使用了哪些数据集/场景，它的 benchmark 是什么，对比了哪些方法
- **数据集**：
  - 种子数据集D共50k样本，来自三部分：
    - 安全数据：22k来自PKU-SafeRLHF（经GPT-4o过滤），3k来自JailbreakV-28k（越狱攻击）。
    - 有用性数据：25k来自UltraFeedback（取最高分和最低分作为chosen/rejected）。
  - 结构化CoT数据DCoT：从PKU-SafeRLHF和UltraFeedback中各取10k，用GPT-4o生成结构化CoT答案。
- **评测基准**：
  - **安全性**：StrongReject（PAIR和PAP两种越狱方式）、XsTest（明显有害查询）、WildChat（高毒性）、Stereotype（Do-Not-Answer中的公平性相关）。
  - **通用能力**：GSM8k（数学）、AlpacaEval 2.0（有用性）、BIG-bench HHH（有用性）、SimpleQA（真实性）、InfoFlow（隐私意识）、AdvGLUE（鲁棒性）。
- **对比方法**：
  - 基线：Base模型、CoT Prompting、SFT、DPO、SACPO（安全约束优化）、Self-Rewarding（自奖励迭代DPO）。
  - 额外对比：开源推理LLM（LLaMA-o1, Skywork-o1, OpenO1, DeepSeek-r1-Distilled, QwQ-32B-Preview）及其通过Deliberative Alignment微调后的版本；商业LLM（GPT-4o, Claude-3, Claude-3.5, Qwen-Max, Gemini-1.5, DeepSeek-R1）。

## 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点
- 论文明确提到：训练在**8块NVIDIA A800 GPU**集群上完成。
- STAIR从零训练大约需要**30小时**（包括SI-MCTS数据生成和迭代DPO）。
- 数据生成阶段：每个prompt构造搜索树约**15秒**，获得一个有效偏好对约**0.47秒**（与自奖励全轨迹采样的0.40秒相当）。
- 推理阶段：额外计算来自更长的推理响应和测试时搜索，文中给出了平均token数和延迟（例如STAIR-DPO-3在StrongReject上平均319.8 token，延迟0.308s；采用Beam Search或BoN时延迟随搜索预算线性增加）。

## 5. 实验数量与充分性：大概做了多少组实验，这些实验是否充分、是否客观、公平
- **主要结果表（Table 1）**：在LLaMA-3.1-8B-Instruct和Qwen-2-7B-Instruct两个模型上，对比了10余种方法（Base、CoT、SFT、DPO、SACPO、Self-Rewarding、STAIR各迭代），在安全性（4个基准）和通用能力（6个基准）上全面报告指标。
- **消融实验**：
  - 步级优化 vs. 全轨迹优化（Table 2）。
  - 迭代训练 vs. 单次迭代多epoch vs. 所有数据单次（Table 2）。
  - 不同奖励函数形式（Table 3）。
  - 自奖励 vs. 训练PRM的测试时扩展（Table 4）。
  - 计算成本分析（Table 5）。
- **与开源推理模型比较**（Table 6）：包括原始o1-like模型和微调后的Deliberative Alignment版本。
- **与商业模型比较**（Table 7）。
- **测试时扩展实验**（Figures 3,4）：展示了在不同搜索预算下（Best-of-N，Beam Search）性能和计算量的变化。
- 实验覆盖全面，对比公平（所有方法在相同种子数据集上训练，评测使用官方实现），指标客观（如Goodness Score、Refusal Rate、Accuracy、Win Rate等）。消融实验有效验证了各组件贡献。

## 6. 论文的主要结论与发现
- STAIR显著提升了模型的安全性，同时在通用能力上也有所改善，缓解了安全-有用性权衡。
- 在StrongReject上，LLaMA-3.1的Goodness Score从0.405提升到0.880（DPO-3），超过所有基线；Qwen-2从0.381提升到0.849。
- 通过迭代自我改进，安全性和有用性持续提高。
- 测试时扩展（Best-of-N、Beam Search）能进一步提升安全性和有用性，且效果随计算量增加而改善。
- 与商业模型比较，STAIR+Beam Search在StrongReject上达到0.939，与Claude-3.5相当（0.936），并大幅超越GPT-4o（0.377）。
- 将推理（系统2思维）引入安全对齐是有效途径，即使基础模型推理能力有限，也能通过STAIR框架获得提升。

## 7. 优点：方法或实验设计上有哪些亮点
- **理论创新**：设计了满足三个期望性质的**安全信息奖励函数**（Safety-Informed Reward），理论推导完整，且实践中简单有效。
- **自洽性**：整个框架不依赖外部标注或昂贵评判器（如GPT-4），通过自生成、自奖励实现迭代改进，成本可控。
- **步级优化**：基于步级偏好数据的DPO提供更细粒度的监督，比全轨迹优化更高效。
- **测试时扩展**：训练过程奖励模型（PRM）并在推理时使用搜索算法，可以动态提升质量，且与模型规模解耦。
- **广泛且严格的实验**：在多个主流安全性和通用基准上评测，与多种开源/商业模型对比，消融分析详尽，结论稳健。
- **开源贡献**：代码、数据集和模型全部开源，便于复现和后续研究。

## 8. 不足与局限
- **计算开销**：SI-MCTS数据生成和迭代训练需要较多离线计算资源（30小时8 GPU），对于资源受限团队可能较高。但论文指出训练是一次性离线进行的，不影响部署。
- **数据集局限性**：训练数据主要来自PKU-SafeRLHF、JailbreakV-28k和UltraFeedback，可能未覆盖所有类型的有害内容（如跨语言、文化特定风险），泛化性有待验证。
- **推理模型依赖**：虽然方法不要求模型具有强推理基础，但实验中仅基于7B/8B模型，在更大模型上效果未知。
- **评估局限**：安全性评估依赖GPT-4o作为评判器（如StrongReject评估），可能有偏差；未进行人工评估；未测试真实交互环境中的越狱鲁棒性。
- **未探讨多模态**：论文仅关注文本场景，未扩展到图像/音频等多模态LLM的安全对齐。
- **应用限制**：测试时扩展增加了推理延迟，在高实时性场景下可能不适用；最佳搜索策略（Beam Search vs Best-of-N）在不同任务上表现不同，需调参。

（完）
