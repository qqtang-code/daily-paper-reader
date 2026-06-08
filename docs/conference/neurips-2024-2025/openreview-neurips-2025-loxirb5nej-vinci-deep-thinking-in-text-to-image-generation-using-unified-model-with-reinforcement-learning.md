---
title: "Vinci: Deep Thinking in Text-to-Image Generation using Unified Model with Reinforcement Learning"
title_zh: Vinci：利用统一模型与强化学习在文本到图像生成中实现深度思考
authors: "Wang Lin, Wentao Hu, Liyu Jia, Kaihang Pan, Zhang Majun, Zhou Zhao, Fei Wu, Jingyuan Chen, Hanwang Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=lOXirB5NeJ"
tags: ["query:mm-cot"]
score: 7.0
evidence: 利用多模态链式推理数据进行冷启动，并采用强化学习实现深度推理
tldr: 现有统一模型未能实现图像生成与理解的端到端集成，缺乏跨模态推理链。论文提出Vinci框架，使用多模态链式推理数据冷启动，再通过强化学习引导生成与理解过程的深度融合。该模型在文本到图像生成和视觉问答等任务上均取得竞争性能，展示了深度推理在跨模态任务中的潜力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-loxirb5nej/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1412, \"height\": 503, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-loxirb5nej/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1378, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-loxirb5nej/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1421, \"height\": 2304, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-loxirb5nej/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1327, \"height\": 724, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-loxirb5nej/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1393, \"height\": 695, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-loxirb5nej/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 642, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-loxirb5nej/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-loxirb5nej/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1429, \"height\": 1444, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-loxirb5nej/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1431, \"height\": 1692, \"label\": \"Table\"}]"
motivation: 统一模型缺乏跨模态推理链和自反思能力，难以实现生成与理解的协同。
method: 采用多模态链式推理冷启动，再通过强化学习优化生成与理解的集成。
result: 在多个生成和理解基准上达到或超过专门模型的效果。
conclusion: 深度推理可以桥接图像生成与理解，提升统一模型的多任务性能。
---

## Abstract
With the continuous development of large language models and reasoning chain technologies, the potential of deep reasoning based on reinforcement learning has shown remarkable promise in multi-task scenarios.  However, existing unified models have yet to achieve end-to-end integration in image generation and understanding tasks, limiting the model’s self-reflection ability and the realization of cross-modal reasoning chains.  To address this, we propose Vinic, a novel framework designed to enable interleaved image generation and understanding through deep reasoning capabilities.  We leverage a small amount of multimodal chain-of-thought (MCoT) data for cold-start and employ reinforcement learning to guide the integration of image generation and understanding tasks.  Additionally, we introduce a momentum-based reward function, which dynamically adjusts the reward distribution by considering historical improvements, ensuring the stability of the model across multiple generations.  Experimental results demonstrate that integrating MCoT can achieve a +22% improvement over the base model on Geneval, effectively enhancing both image generation quality and instruction alignment capabilities.

---

## 论文详细总结（自动生成）

# 论文总结：Vinci: 深度思考在文本到图像生成中的应用（统一模型+强化学习）

## 1. 核心问题与整体含义（研究动机与背景）
- **问题**：现有统一模型（如Janus-Pro、Show-o）在图像生成与理解任务中未能实现真正的端到端集成——图像在模型内部有两种不同的表示方式，导致模型无法直接理解自己生成的图像，从而限制了自我反思能力和跨模态推理链的发挥。  
- **背景**：大语言模型与链式推理（CoT）技术在数学、代码等单模态任务上展现了深度推理的潜力；但在跨模态图像生成中，已有工作（如T2I-R1）仅进行语义级或令牌级的单模态CoT，缺乏对生成结果的实时观察与迭代优化。  
- **意义**：该论文旨在实现一种**多模态链式推理（MCoT）**能力，让模型在生成过程中能够“看见”并反思自己的输出，从而深度融合图像生成与理解，提升指令跟随和生成质量。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：将图像生成任务转化为一个多步推理过程：模型先生成中间图像 → 观察结果并分析问题（如颜色错误、物体缺失）→ 描述改进策略 → 生成下一张图像，重复直至满意。  
- **关键技术**：
  1. **冷启动（Cold Start）**  
     - 利用少量（2万条）人工构建的MCoT数据对模型进行初步微调，使其学会输出格式和多步反思流程。  
     - MCoT数据构造三阶段：  
       * 生成候选图像（Flux模型）→ 目标检测（Mask2Former）获得物体列表；  
       * 用多模态大模型（Qwen-VL）对每张图像标注描述和得分；  
       * 按得分排序后随机选取k步，保证最后一步是高分图像，构造出“初始图像→反思文本→改进图像”的序列。  
  2. **强化学习（RL）阶段**  
     - 基于GRPO（Group Relative Policy Optimization）框架，无需批评模型。  
     - 每步生成G个候选，用归一化优势计算并加上KL散度惩罚。  
     - **奖励函数三部分**：  
       * *程序级奖励（Ri）*：用目标检测模型（MMDetection）检查生成的图像是否满足提示中的物体数量、颜色等条件，返回0/1得分；  
       * *问答级奖励（Rt）*：用多模态大模型评估生成的文本（反思描述）是否完整、准确、包含改进策略，三项各0-2分取平均；  
       * *动量过程奖励（Rm）*：基于历史改进趋势动态调整，公式为 \[ R_m = \frac{1}{n}\sum_{t=1}^n R_i(s_t) + \alpha \sum_{k=1}^{n-1} \frac{\Delta_k}{\sqrt{V_k}+\epsilon} \lambda^{k-1} \]，其中 \(\Delta_k = \max(0, R_i(s_k)-R_i(s_{k-1}))\)，\(V_k\) 为指数移动平均方差。该奖励鼓励持续稳定的进步，避免单次跳变。  
     - 总奖励 \(R = R_i + R_t + R_m\)。

## 3. 实验设计
- **数据集**：  
  - 冷启动：从Flux生成图像、Qwen-VL标注的2万条MCoT数据（含1步、2步、3步推理）。  
  - RL阶段：3万条纯文本提示（无对应图像），与GenEval测试集严格去重。  
- **基准（Benchmark）**：GenEval——评估文本到图像对齐能力，包含单物体、双物体、计数、颜色、位置、颜色属性等子任务。  
- **对比方法**：  
  - 仅生成模型：PixArt-α、SDXL、FLUX.1-dev、DALL-E 3、CogView4-6B、SD3-Medium。  
  - 统一模型（生成+理解）：SEED-X、Emu3-Gen（本文基线）、TokenFlow-XL、Transfusion、D-DiT、Show-o、ILLUME+、Infinity、Janus-Pro-7B、GPT-4o。  
- **主要结果**（表1）：Vinci在总体得分0.76，仅次于Janus-Pro-7B（0.80）和GPT-4o（0.85），显著超过基线Emu3-Gen（0.54），提升幅度达+22%。尤其在“位置”（0.17→0.86）和“颜色属性”（0.21→0.54）上提升巨大。  
- **消融实验**（表2）：逐步添加奖励函数：  
  - 仅Rt → 0.59（位置提升）；  
  - 仅Ri → 0.66（计数、颜色提升）；  
  - Ri+Rt → 0.71；  
  - 全量（Ri+Rt+Rm）→ 0.76。  
  验证了图像理解能力反哺生成、显式图像反馈和稳定迭代的重要性。  
- **可视化案例**（图3、图4）：展示了Vinci对复杂位置指令（如“tv remote below a cow”）的准确执行，以及变长推理过程（简单任务一步完成，复杂任务2-3步反思）。

## 4. 资源与算力
- **GPU**：16张A800 GPU。  
- **训练时长**：冷启动阶段约20小时（batch size=64），RL阶段约60小时（group size=8）。  
- **模型基础**：Emu3-Gen，上下文长度扩展至15360 tokens，支持约3次迭代。  
- **说明**：文中明确给出了训练硬件和时间，计算资源中等。

## 5. 实验数量与充分性
- **实验组数**：主要性能对比表1涵盖15+种方法；消融表2有5组对比；还有MCoT类型分布统计、提示模板示例等附录。  
- **充分性**：  
  - 覆盖了主流生成模型和统一模型，对比全面；  
  - 消融实验系统解耦了各奖励函数的贡献，验证了设计合理性；  
  - 提供了定性可视化，展示了推理过程。  
- **客观性与公平性**：  
  - 使用标准公开基准GenEval；  
  - 训练提示与测试集去重，避免数据泄露；  
  - 基线模型选择合理，包括最先进的GPT-4o和Janus-Pro。  
  - **不足**：未报告置信区间/误差棒，单次运行结果可能存在波动；无人类评估。

## 6. 主要结论与发现
- **深度推理有效**：多模态链式推理（MCoT）显著提升了统一模型在生成任务中的指令跟随性能，总体提升+22%。  
- **动量奖励稳定训练**：动量过程奖励函数（Rm）通过历史改进动态调节，增强了训练的稳定性和最终质量。  
- **图像理解反哺生成**：即使只使用文本质量奖励（Rt），也能改善图像生成，说明理解能力的提升可正向迁移。  
- **变长推理自适应**：模型能根据任务难度自动决定推理步数（1-3步），在效率和效果间取得平衡。

## 7. 优点
- **创新性**：首次将“深度思考”概念引入图像生成，实现端到端的生成-理解-反思闭环。  
- **方法论设计**：冷启动+RL的两阶段训练策略，既保证了初期稳定性，又通过RL引导长程推理；动量奖励函数灵感来源于Adam优化器，设计精巧。  
- **实验充分**：覆盖多种模型类型，消融实验清晰揭示各组件贡献；可视化直观展示推理过程。  
- **实用性**：在标准基准上达到竞争性结果，且训练开销可接受，易于复现。

## 8. 不足与局限
- **性能天花板**：在GenEval上仍落后于Janus-Pro-7B和GPT-4o，尤其是计数任务（0.48 vs GPT-4o的0.85），说明模型对精细数量关系的推理仍有不足。  
- **上下文限制**：扩展至15360 tokens仅支持约3次迭代，更长的推理链受限于自回归模型的上下文窗口；未来需改进图像令牌压缩或注意力机制。  
- **基础模型依赖**：基于Emu3-Gen，其统一表示（离散视觉令牌）本身有信息损失；若采用更强大的基础模型（如Janus-Pro），可能进一步提升。  
- **数据工程成本**：MCoT数据依赖外部生成模型和检测模型，存在级联错误；冷启动数据仅2万条，规模较小。  
- **评估局限**：仅用GenEval基准，缺乏多样性设置（如开放域生成质量、用户偏好等）；未进行人工评估或置信区间报告。  
- **潜在风险**：强生成+理解能力可能被误用于生成误导性内容（深伪等），论文在附录中讨论了社会影响，但未提出具体缓解措施。

（完）
