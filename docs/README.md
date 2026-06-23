<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-23
- 运行时间：2026-06-23 21:44:27 UTC
- 运行状态：成功
- 本次总论文数：24
- 精读区：12
- 速读区：12

### 今日简报（AI）
今日共处理24篇论文，精读两篇9.0分佳作，涵盖生成式视觉思维链与分组查询专家注意力机制，速读三篇8.0分工作聚焦多模态自蒸馏、CPU-GPU协同KV缓存及南亚内窥镜数据集。  
最值得关注的方向包括：基于扩散模型RGB中间表示的生成式视觉思维链（Gen-VCoT）以及GQA自注意力中的混合专家架构（Grouped Query Experts），这两项分别从视觉推理和多头注意力效率上带来突破。  
建议普通读者优先透视视觉推理与注意力机制的最新进展，后续可跟踪扩散模型在视觉-语言任务中的集成应用，以及面向长序列推理的硬件协同优化思路。
- 详情：[/202606/23/README](/202606/23/README)

### 精读区论文标签
1. [Gen-VCoT: Generative Visual Chain-of-Thought Reasoning via Diffusion-Based RGB Intermediate Representations](/202606/23/2606.16783v1-gen-vcot-generative-visual-chain-of-thought-reasoning-via-diffusion-based-rgb-intermediate-representations)  
   标签：评分：9.0/10、query:mm-cot
   evidence：基于视觉中间表示的多模态链式推理
2. [Grouped Query Experts: Mixture-of-Experts on GQA Self-Attention](/202606/23/2606.20945v1-grouped-query-experts-mixture-of-experts-on-gqa-self-attention)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：通过分组查询专家实现KV缓存压缩
3. [Extraction and Analysis of Multimodal Concepts in Vision Language Models through Sparse Autoencoders](/202606/23/2606.21197v1-extraction-and-analysis-of-multimodal-concepts-in-vision-language-models-through-sparse-autoencoders)  
   标签：评分：9.0/10、query:multimodal
   evidence：使用稀疏自编码器提取视觉语言模型中的多模态概念
4. [Recency/Frequency Adaptive KV Caching for Large Language Model Serving](/202606/23/2606.21238v1-recencyfrequency-adaptive-kv-caching-for-large-language-model-serving)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于近期和频率的自适应KV缓存用于LLM服务
5. [Fast-TurboQuant: A Multiplier-Free Online Vector Quantization Approach](/202606/23/2606.21448v1-fast-turboquant-a-multiplier-free-online-vector-quantization-approach)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：Fast-TurboQuant为KV缓存压缩提供免乘法向量量化
6. [Keyless Attention: Value-Space Routing and Value-Only Caching for Efficient Transformers](/202606/23/2606.21848v1-keyless-attention-value-space-routing-and-value-only-caching-for-efficient-transformers)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：提出无键注意力与仅值缓存，KV缓存内存减少50%
7. [Look Light, Think Heavy: What Multimodal Chain-of-Thought Reasoning Can and Cannot Do](/202606/23/2606.22565v1-look-light-think-heavy-what-multimodal-chain-of-thought-reasoning-can-and-cannot-do)  
   标签：评分：9.0/10、query:mm-cot
   evidence：多模态链式思维推理效果分析
8. [SpotAttention: Plug-In Block-Sparse Routing for Pretrained Long-Context Transformers](/202606/23/2606.22874v1-spotattention-plug-in-block-sparse-routing-for-pretrained-long-context-transformers)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：长上下文Transformer的块稀疏路由
9. [ScalingAttention: Discovering Intrinsic Sparse Attention Topology for Video Diffusion Transformers](/202606/23/2606.23019v1-scalingattention-discovering-intrinsic-sparse-attention-topology-for-video-diffusion-transformers)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：发现视频扩散Transformer中的内在稀疏注意力拓扑
10. [SPAR: Semantic-Pixel Self-Alignment and Adaptive Routing for Unified Multimodal Models](/202606/23/2606.23041v1-spar-semantic-pixel-self-alignment-and-adaptive-routing-for-unified-multimodal-models)  
   标签：评分：9.0/10、query:multimodal
   evidence：统一多模态框架，包含语义-像素对齐和自适应路由
11. [MotionHalluc: Diagnosing Kinematic Hallucinations in Fine-Grained Motion Reasoning](/202606/23/2606.23061v1-motionhalluc-diagnosing-kinematic-hallucinations-in-fine-grained-motion-reasoning)  
   标签：评分：9.0/10、query:multimodal
   evidence：视频比较中运动幻觉诊断基准
12. [Kamera: Unified Position-Invariant Multimodal KV Cache for Training-Free Reuse](/202606/23/2606.23581v1-kamera-unified-position-invariant-multimodal-kv-cache-for-training-free-reuse)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：多模态KV缓存压缩与免训练重用

### 速读区论文标签
1. [Seeing Before Reasoning: Decoupling Perception and Reasoning for Shortcut-Resilient Multimodal On-Policy Self-Distillation](/202606/23/2606.19120v2-seeing-before-reasoning-decoupling-perception-and-reasoning-for-shortcut-resilient-multimodal-on-policy-self-distillation)  
   标签：评分：8.0/10、query:multimodal
   evidence：解耦感知与推理以减轻多模态大模型幻觉
2. [HERALD: High-Throughput Block Diffusion LLM Serving via CPU-GPU Cooperative KV Cache Retrieval](/202606/23/2606.21633v1-herald-high-throughput-block-diffusion-llm-serving-via-cpu-gpu-cooperative-kv-cache-retrieval)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：KV缓存卸载与稀疏检索用于块扩散LLM
3. [SAGE: An Expert-Annotated South Asian GI Endoscopy Dataset for Multimodal Learning and Hallucination Analysis](/202606/23/2606.22144v1-sage-an-expert-annotated-south-asian-gi-endoscopy-dataset-for-multimodal-learning-and-hallucination-analysis)  
   标签：评分：8.0/10、query:multimodal
   evidence：用于内窥镜多模态学习和幻觉分析的数据集
4. [OmniSpace: Efficient Geometry Awareness for Autonomous Vehicles MLLMs](/202606/23/2606.22617v1-omnispace-efficient-geometry-awareness-for-autonomous-vehicles-mllms)  
   标签：评分：8.0/10、query:multimodal
   evidence：面向MLLMs的几何感知空间推理
5. [Mixtures of Subspaces for Bandwidth Efficient Context Parallel Training](/202606/23/2606.16384v1-mixtures-of-subspaces-for-bandwidth-efficient-context-parallel-training)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：通过低秩结构实现长上下文训练中的通信压缩
6. [CulMind: Benchmarking Multimodal Understanding and Reasoning in Chinese Cultural Heritage](/202606/23/2606.21618v1-culmind-benchmarking-multimodal-understanding-and-reasoning-in-chinese-cultural-heritage)  
   标签：评分：7.0/10、query:multimodal
   evidence：中国文化遗产多模态理解与推理基准
7. [Look Before You Zoom: Adaptive Routing for the Resolution-Context Trade-off in Visual RAG](/202606/23/2606.21968v1-look-before-you-zoom-adaptive-routing-for-the-resolution-context-trade-off-in-visual-rag)  
   标签：评分：7.0/10、query:multimodal
   evidence：视觉RAG中分辨率-上下文权衡的自适应路由
8. [Gold Points Sniper: Self-guided Visual Reasoning in VLM for Fine-grained Action Understanding](/202606/23/2606.22409v1-gold-points-sniper-self-guided-visual-reasoning-in-vlm-for-fine-grained-action-understanding)  
   标签：评分：7.0/10、query:multimodal
   evidence：VLM中用于细粒度动作理解的视觉推理
9. [Decoupling Semantics from Distortions: Multi-Scale Two-Stream Vision-Language Alignment for AI-Generated Image Quality Assessment](/202606/23/2606.16799v1-decoupling-semantics-from-distortions-multi-scale-two-stream-vision-language-alignment-for-ai-generated-image-quality-assessment)  
   标签：评分：6.0/10、query:multimodal
   evidence：多尺度视觉-语言对齐用于图像质量评估
10. [FiLM-Coordinated Dual-Branch Transformer for Global-Local Dependency Modeling in Language Modeling](/202606/23/2606.21075v1-film-coordinated-dual-branch-transformer-for-global-local-dependency-modeling-in-language-modeling)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：通过双分支FiLM协调的高效注意力
11. [Compressing Observation History into Agent Memory: Distilling Transformers into Recurrent Transformers](/202606/23/2606.21562v1-compressing-observation-history-into-agent-memory-distilling-transformers-into-recurrent-transformers)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：将观察历史压缩到循环记忆，类似于Transformer的KV缓存压缩
12. [Pre-Generation Hallucination Detection in Large Language Models via Soft-Target Attention Probing](/202606/23/2606.21917v1-pre-generation-hallucination-detection-in-large-language-models-via-soft-target-attention-probing)  
   标签：评分：6.0/10、query:multimodal
   evidence：通过注意力探针检测大语言模型中的幻觉


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
