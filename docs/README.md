<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-20
- 运行时间：2026-06-20 21:40:45 UTC
- 运行状态：成功
- 本次总论文数：19
- 精读区：7
- 速读区：12

### 今日简报（AI）
今天精读了两篇9分论文，聚焦视觉推理链与Transformer剪枝，速读涵盖边缘端LoRA显存优化、VLM视觉上下文演化等方向。  
最值得关注的是《Gen-VCoT》的扩散RGB中间表示实现可视化思维链，以及《Complementary Attention Head Pruning》的互补注意力头剪枝方法。  
建议优先精读这两篇高分论文，把握视觉推理新范式和Transformer高效化技巧，对实际模型压缩与多模态理解有直接启发。
- 详情：[/202606/20/README](/202606/20/README)

### 精读区论文标签
1. [Gen-VCoT: Generative Visual Chain-of-Thought Reasoning via Diffusion-Based RGB Intermediate Representations](/202606/20/2606.16783v1-gen-vcot-generative-visual-chain-of-thought-reasoning-via-diffusion-based-rgb-intermediate-representations)  
   标签：评分：9.0/10、query:mm-cot
   evidence：提出了Gen-VCoT，使用RGB中间表示进行视觉链式推理；直接匹配多模态链式推理要求
2. [Complementary Attention Head Pruning for Efficient Transformers](/202606/20/2606.19150v1-complementary-attention-head-pruning-for-efficient-transformers)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向高效Transformer的注意力头剪枝
3. [Language-Instructed Vision Embeddings for Controllable and Generalizable Perception](/202606/20/2606.19584v1-language-instructed-vision-embeddings-for-controllable-and-generalizable-perception)  
   标签：评分：9.0/10、query:multimodal
   evidence：语言指导的视觉嵌入减少多模态模型幻觉
4. [Timage: A Generative Text-in-Image Paradigm for Fine-Tuning Vision-Language Models](/202606/20/2606.19944v1-timage-a-generative-text-in-image-paradigm-for-fine-tuning-vision-language-models)  
   标签：评分：9.0/10、query:multimodal
   evidence：通过在输入层对齐文本与图像来提升多模态理解
5. [DLWM: Diverse Latent World Models for Efficient Multimodal Reasoning](/202606/20/2606.15160v1-dlwm-diverse-latent-world-models-for-efficient-multimodal-reasoning)  
   标签：评分：8.0/10、query:mm-cot
   evidence：多样潜在世界模型用于高效多模态推理
6. [Seeing Before Reasoning: Decoupling Perception and Reasoning for Shortcut-Resilient Multimodal On-Policy Self-Distillation](/202606/20/2606.19120v1-seeing-before-reasoning-decoupling-perception-and-reasoning-for-shortcut-resilient-multimodal-on-policy-self-distillation)  
   标签：评分：8.0/10、query:mm-cot
   evidence：解耦感知与推理，实现多模态自我蒸馏中的逐步推理
7. [PerceptionDLM: Parallel Region Perception with Multimodal Diffusion Language Models](/202606/20/2606.19534v1-perceptiondlm-parallel-region-perception-with-multimodal-diffusion-language-models)  
   标签：评分：8.0/10、query:multimodal
   evidence：多模态扩散语言模型实现并行区域感知

### 速读区论文标签
1. [Techniques for Peak Memory Reduction for LoRA Fine-tuning of LLMs on Edge Devices](/202606/20/2606.19528v1-techniques-for-peak-memory-reduction-for-lora-fine-tuning-of-llms-on-edge-devices)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：提出了基于令牌子集的softmax近似（稀疏）和激活缓存；直接减少大语言模型微调的内存占用
2. [The Hidden Evolution of Disguised Visual Context inside the VLM](/202606/20/2606.20077v1-the-hidden-evolution-of-disguised-visual-context-inside-the-vlm)  
   标签：评分：8.0/10、query:multimodal
   evidence：VLM集成架构对视觉上下文影响的比较
3. [One Layer's Trash is Another Layer's Treasure: Adaptive Layer-wise Visual Token Selection in LVLMs](/202606/20/2606.14277v1-one-layers-trash-is-another-layers-treasure-adaptive-layer-wise-visual-token-selection-in-lvlms)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：自适应逐层视觉令牌剪枝以提升LVLM效率
4. [Stepwise Token Selection for Efficient Multimodal Large Language Models](/202606/20/2606.16067v1-stepwise-token-selection-for-efficient-multimodal-large-language-models)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：逐步视觉令牌选择提升多模态大语言模型效率
5. [Mixtures of Subspaces for Bandwidth Efficient Context Parallel Training](/202606/20/2606.16384v1-mixtures-of-subspaces-for-bandwidth-efficient-context-parallel-training)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：针对上下文并行的压缩方法，利用低秩结构
6. [MMDiff: Extending Diffusion Transformers for Multi-Modal Generation](/202606/20/2606.16673v1-mmdiff-extending-diffusion-transformers-for-multi-modal-generation)  
   标签：评分：7.0/10、query:multimodal
   evidence：扩展扩散变换器用于多模态生成，与多模态架构相关
7. [Context-Aware RL for Agentic and Multimodal LLMs](/202606/20/2606.17053v1-context-aware-rl-for-agentic-and-multimodal-llms)  
   标签：评分：7.0/10、query:multimodal
   evidence：提出了上下文感知强化学习以改进多模态推理和长程锚定能力
8. [VL-MemKnG: Hybrid Memory with a Spatio-Temporal Knowledge Graph for Question Answering over Long Egocentric Navigation Trajectories](/202606/20/2606.17183v1-vl-memkng-hybrid-memory-with-a-spatio-temporal-knowledge-graph-for-question-answering-over-long-egocentric-navigation-trajectories)  
   标签：评分：7.0/10、query:multimodal
   evidence：混合记忆与时空知识图用于长视频问答
9. [RepFusion: Leveraging Multimodal Priors for Denoising in Representation Space](/202606/20/2606.14700v1-repfusion-leveraging-multimodal-priors-for-denoising-in-representation-space)  
   标签：评分：6.0/10、query:multimodal
   evidence：利用MLLM作为噪声表征编码器用于文本到图像生成中的去噪
10. [RATS! Patches Talk Through Registers: Emergent Parts in Register Attention Transformers](/202606/20/2606.14701v1-rats-patches-talk-through-registers-emergent-parts-in-register-attention-transformers)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：提出了带压缩-通信-广播注意力模式的注册注意力变换器；与高效注意力相关
11. [Cascaded Sparse Autoencoders Learn Multi-Level Visual Concepts in Multimodal LLMs](/202606/20/2606.16193v1-cascaded-sparse-autoencoders-learn-multi-level-visual-concepts-in-multimodal-llms)  
   标签：评分：6.0/10、query:multimodal
   evidence：级联稀疏自编码器学习多模态大语言模型中的层次视觉概念
12. [Attention Alignment Between Humans and Vision-Language Models](/202606/20/2606.17410v1-attention-alignment-between-humans-and-vision-language-models)  
   标签：评分：6.0/10、query:multimodal
   evidence：视觉语言模型中的注意力对齐


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
