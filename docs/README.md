<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-17
- 运行时间：2026-06-17 22:31:15 UTC
- 运行状态：成功
- 本次总论文数：27
- 精读区：15
- 速读区：12

### 今日简报（AI）
今日日报聚焦多模态大模型优化，精读10分论文《边界注意力校准压缩KV缓存》，速读涉及表格-图像适配器调优、视频幻觉修补及视觉原生智能搜索。最值得关注边界注意力校准（BAC）高效压缩KV缓存，以及视频标记修补（MultiToP）和主动视觉推理（Visual-Seeker）方向。建议优先研读BAC在内存受限场景的应用原理，同时跟进适配器调优与视觉搜索的实践方案。
- 详情：[/202606/17/README](/202606/17/README)

### 精读区论文标签
1. [Last But Not Least: Boundary Attention CalibratiON for Multimodal KV Cache Compression](/202606/17/2606.14782v1-last-but-not-least-boundary-attention-calibration-for-multimodal-kv-cache-compression)  
   标签：评分：10.0/10、query:sparse-attn
   evidence：多模态KV缓存压缩，使用边界注意力校准
2. [Last But Not Least: Boundary Attention CalibratiON for Multimodal KV Cache Compression](/202606/17/2606.14782v2-last-but-not-least-boundary-attention-calibration-for-multimodal-kv-cache-compression)  
   标签：评分：10.0/10、query:sparse-attn
   evidence：多模态KV缓存压缩，使用边界注意力校准
3. [miniReranker: Efficient Multimodal Reranking through Visual Cache Reuse and Interaction Sparsity](/202606/17/2606.10759v2-minireranker-efficient-multimodal-reranking-through-visual-cache-reuse-and-interaction-sparsity)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：多模态重排序中的视觉缓存重用与交互稀疏性
4. [ARM: An AutoRegressive Large Multimodal Model with Unified Discrete Representations](/202606/17/2606.11188v1-arm-an-autoregressive-large-multimodal-model-with-unified-discrete-representations)  
   标签：评分：9.0/10、query:multimodal
   evidence：统一多模态理解和生成模型
5. [MultiToP: Learning to Patch Visual Tokens to Mitigate Hallucinations in Video Large Multimodal Models](/202606/17/2606.11792v1-multitop-learning-to-patch-visual-tokens-to-mitigate-hallucinations-in-video-large-multimodal-models)  
   标签：评分：9.0/10、query:multimodal
   evidence：视觉令牌修补缓解视频大多模态模型中的幻觉
6. [HYDRA-X: Native Unified Multimodal Models with Holistic Visual Tokenizers](/202606/17/2606.13289v1-hydra-x-native-unified-multimodal-models-with-holistic-visual-tokenizers)  
   标签：评分：9.0/10、query:multimodal
   evidence：统一的视觉分词器多模态模型，融合图像和视频
7. [PolyKV: Heterogeneous Retention and Allocation for KV Cache Compression](/202606/17/2606.15157v1-polykv-heterogeneous-retention-and-allocation-for-kv-cache-compression)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：逐层异构KV缓存压缩，包括方法选择和预算分配
8. [DLWM: Diverse Latent World Models for Efficient Multimodal Reasoning](/202606/17/2606.15160v1-dlwm-diverse-latent-world-models-for-efficient-multimodal-reasoning)  
   标签：评分：9.0/10、query:mm-cot
   evidence：多样潜在世界模型实现高效多模态推理，类似链式思维
9. [Rethinking the Role of Efficient Attention in Hybrid Architectures](/202606/17/2606.15378v1-rethinking-the-role-of-efficient-attention-in-hybrid-architectures)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：混合架构中高效注意力的系统分析
10. [Mitigating Visual Hallucinations in Multimodal Systems through Retrieval-Augmented Reliability-Aware Inference](/202606/17/2606.15782v1-mitigating-visual-hallucinations-in-multimodal-systems-through-retrieval-augmented-reliability-aware-inference)  
   标签：评分：9.0/10、query:multimodal
   evidence：通过检索增强的可靠性感知推理缓解多模态系统视觉幻觉
11. [Training-free sparse attention based on cumulative energy filtering](/202606/17/2606.16317v1-training-free-sparse-attention-based-on-cumulative-energy-filtering)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于累积能量滤波的训练无关稀疏注意力用于DiTs
12. [Pareto LoRA: Mitigating Modality Imbalance in Unified Multimodal Models via Pareto-Optimal Gradient Integration](/202606/17/2606.17296v1-pareto-lora-mitigating-modality-imbalance-in-unified-multimodal-models-via-pareto-optimal-gradient-integration)  
   标签：评分：9.0/10、query:multimodal
   evidence：统一多模态模型中的模态不平衡，提出帕累托最优梯度整合的LoRA方法
13. [MODE-RAG: Manifold Outlier Diagnosis and Energy-based Retrieval-Augmented Generation Evaluation](/202606/17/2606.17449v1-mode-rag-manifold-outlier-diagnosis-and-energy-based-retrieval-augmented-generation-evaluation)  
   标签：评分：9.0/10、query:multimodal
   evidence：通过多智能体系统检测和缓解多模态幻觉
14. [AnchorKV: Safety-Aware KV Cache Compression via Soft Penalty with a Refusal Anchor](/202606/17/2606.17872v1-anchorkv-safety-aware-kv-cache-compression-via-soft-penalty-with-a-refusal-anchor)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：安全感知的KV缓存压缩
15. [ConSA: Controllable Sparsity in Hybrid Attention via Learnable Allocation](/202606/17/2606.18056v1-consa-controllable-sparsity-in-hybrid-attention-via-learnable-allocation)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：混合注意力中的可学习稀疏分配

### 速读区论文标签
1. [Parameter-Efficient Adapter Tuning for Tabular-Image Multimodal Learning](/202606/17/2606.11682v1-parameter-efficient-adapter-tuning-for-tabular-image-multimodal-learning)  
   标签：评分：8.0/10、query:multimodal
   evidence：基于适配器的多模态学习微调，结合表格和图像数据
2. [MultiToP: Learning to Patch Visual Tokens to Mitigate Hallucinations in Video Large Multimodal Models](/202606/17/2606.11792v2-multitop-learning-to-patch-visual-tokens-to-mitigate-hallucinations-in-video-large-multimodal-models)  
   标签：评分：8.0/10、query:multimodal
   evidence：通过token修补缓解视频多模态模型幻觉
3. [Visual-Seeker: Towards Visual-Native Multimodal Agentic Search via Active Visual Reasoning](/202606/17/2606.15231v1-visual-seeker-towards-visual-native-multimodal-agentic-search-via-active-visual-reasoning)  
   标签：评分：8.0/10、query:multimodal
   evidence：主动视觉推理用于多模态搜索
4. [From Frames to Temporal Graphs: In-Context Egocentric Action Recognition with Vision-Language Models](/202606/17/2606.15417v1-from-frames-to-temporal-graphs-in-context-egocentric-action-recognition-with-vision-language-models)  
   标签：评分：8.0/10、query:mm-cot
   evidence：通过时间动作图实现少样本第一人称动作识别，支持链式推理
5. [Boltzmann Attention: Learnable Ising Couplings for Cooperative Attention](/202606/17/2606.12478v1-boltzmann-attention-learnable-ising-couplings-for-cooperative-attention)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：具有可学习成对耦合的新型注意力机制
6. [PRISMR: Overcoming Parse Collapse in Multimodal Listwise Ranking via Parameterized Representation Internalization](/202606/17/2606.12942v1-prismr-overcoming-parse-collapse-in-multimodal-listwise-ranking-via-parameterized-representation-internalization)  
   标签：评分：7.0/10、query:multimodal
   evidence：解决多模态列表排序中的解析崩溃问题，与多模态理解相关
7. [GIVE: Grounding Human Gestures in Vision-Language-Action Models](/202606/17/2606.13435v1-give-grounding-human-gestures-in-vision-language-action-models)  
   标签：评分：7.0/10、query:multimodal
   evidence：在不改变模型架构的前提下将人类手势理解集成到VLA模型中
8. [Context-aware Modality-Topology Co-Alignment for Multimodal Attributed Graphs](/202606/17/2606.14172v1-context-aware-modality-topology-co-alignment-for-multimodal-attributed-graphs)  
   标签：评分：7.0/10、query:multimodal
   evidence：多模态属性图学习，任务自适应上下文对齐
9. [AnyMod-LLVE: Low-Light Video Enhancement with Modality-Agnostic Inference](/202606/17/2606.11186v1-anymod-llve-low-light-video-enhancement-with-modality-agnostic-inference)  
   标签：评分：6.0/10、query:multimodal
   evidence：处理缺失模态的多模态架构
10. [Magnifying What Matters: Attention-Guided Adaptive Rendering for Visual Text Comprehension](/202606/17/2606.12898v1-magnifying-what-matters-attention-guided-adaptive-rendering-for-visual-text-comprehension)  
   标签：评分：6.0/10、query:multimodal
   evidence：视觉文本理解中的多模态理解
11. [An Attention-based Model for Robust Forecasting with Missing Modality](/202606/17/2606.13970v1-an-attention-based-model-for-robust-forecasting-with-missing-modality)  
   标签：评分：6.0/10、query:multimodal
   evidence：基于注意力的缺失模态鲁棒多模态模型
12. [Beyond Scalar Distances: Semantic Attribute Gradients from Frozen MLLMs for Visual Embeddings](/202606/17/2606.15134v1-beyond-scalar-distances-semantic-attribute-gradients-from-frozen-mllms-for-visual-embeddings)  
   标签：评分：6.0/10、query:multimodal
   evidence：利用多模态大语言模型改进视觉嵌入


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
