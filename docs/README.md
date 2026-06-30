<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-30
- 运行时间：2026-06-30 22:22:57 UTC
- 运行状态：成功
- 本次总论文数：23
- 精读区：11
- 速读区：12

### 今日简报（AI）
今日推荐23篇注意力机制优化论文，精读重点聚焦静态稀疏注意力与无注意力矩阵的KV缓存淘汰。最值得关注的是Depth-Staggered Fibonacci Spacing在稀疏注意力中超越学习扩张，以及Epiphany-Aware KV缓存在不依赖注意力矩阵下的高效淘汰。建议读者优先关注静态调度策略与传统稀疏方法的对比实验，以及KV缓存优化对长上下文推理的实际影响。
- 详情：[/202606/30/README](/202606/30/README)

### 精读区论文标签
1. [Depth-Staggered Fibonacci Spacing for Sparse Attention: Static Schedules Beat Learned Dilation and Extrapolate Where Dense Attention Fails](/202606/30/2606.28560v1-depth-staggered-fibonacci-spacing-for-sparse-attention-static-schedules-beat-learned-dilation-and-extrapolate-where-dense-attention-fails)  
   标签：评分：10.0/10、query:sparse-attn
   evidence：使用斐波那契间隔偏移和静态调度的稀疏自注意力
2. [Epiphany-Aware KV Cache Eviction Without the Attention Matrix](/202606/30/2606.26472v2-epiphany-aware-kv-cache-eviction-without-the-attention-matrix)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于顿悟分数的KV缓存逐出，无需注意力矩阵
3. [Enhancing Layer Interaction Using Key-Correlated Layer Attention](/202606/30/2606.28405v1-enhancing-layer-interaction-using-key-correlated-layer-attention)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：关键相关层注意力实现线性复杂度，用于高效Transformer设计
4. [Detecting Clinical Hallucinations in LVLMs via Counterfactual Visual Grounding Uncertainty](/202606/30/2606.28520v1-detecting-clinical-hallucinations-in-lvlms-via-counterfactual-visual-grounding-uncertainty)  
   标签：评分：9.0/10、query:multimodal
   evidence：通过视觉接地检测LVLM幻觉
5. [HARD-KV: Head-Adaptive Regularization for Decoding-time KV Compression](/202606/30/2606.28831v1-hard-kv-head-adaptive-regularization-for-decoding-time-kv-compression)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：解码时KV压缩的头自适应正则化
6. [KernelFlume: Elastic Core-Attention Scaling for Agentic Long-Context Decoding](/202606/30/2606.29207v1-kernelflume-elastic-core-attention-scaling-for-agentic-long-context-decoding)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：将注意力计算分离以弹性缩放KV缓存，用于长上下文解码
7. [Enhancing Part-Level Point Grounding for Any Open-Source MLLMs](/202606/30/2606.29267v1-enhancing-part-level-point-grounding-for-any-open-source-mllms)  
   标签：评分：9.0/10、query:multimodal
   evidence：增强任意开源多模态大模型的部件级点定位
8. [FADE: Mitigating Hallucinations by Reducing Language-Prior Dominance in Large Vision-Language Models](/202606/30/2606.29431v1-fade-mitigating-hallucinations-by-reducing-language-prior-dominance-in-large-vision-language-models)  
   标签：评分：9.0/10、query:multimodal
   evidence：分析FFN中语言先验主导作为幻觉原因并提出缓解方法
9. [Coverage-Driven KV Cache Eviction for Efficient and Improved Inference of LLM](/202606/30/2606.29563v1-coverage-driven-kv-cache-eviction-for-efficient-and-improved-inference-of-llm)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：覆盖驱动的KV缓存驱逐策略，减少内存同时保持长上下文推理性能
10. [Clearer Sight, Fewer Lies: Oriented Pickup Preference Optimization for Multimodal Hallucination Mitigation](/202606/30/2606.29805v1-clearer-sight-fewer-lies-oriented-pickup-preference-optimization-for-multimodal-hallucination-mitigation)  
   标签：评分：9.0/10、query:multimodal
   evidence：通过偏好优化缓解多模态幻觉
11. [Predict, Reuse, and Repair: Accelerating Dynamic Sparse Attention for Long-Context LLM Decoding](/202606/30/2606.30389v1-predict-reuse-and-repair-accelerating-dynamic-sparse-attention-for-long-context-llm-decoding)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：直接处理长上下文LLM解码中的动态稀疏注意力，使用预测和推测加速

### 速读区论文标签
1. [IV-CoT: Implicit Visual Chain-of-Thought for Structure-Aware Text-to-Image Generation](/202606/30/2606.24849v1-iv-cot-implicit-visual-chain-of-thought-for-structure-aware-text-to-image-generation)  
   标签：评分：8.0/10、query:mm-cot
   evidence：面向多模态生成的隐式视觉思维链
2. [CARVE: Content-Aware Recurrent with Value Efficiency for Chunk-Parallel Linear Attention](/202606/30/2606.27229v2-carve-content-aware-recurrent-with-value-efficiency-for-chunk-parallel-linear-attention)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：内容感知递归与值效率的块并行线性注意力
3. [Flexformer: Flexible Linear Transformer with Learnable Attention Kernel](/202606/30/2606.27748v2-flexformer-flexible-linear-transformer-with-learnable-attention-kernel)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：可学习注意核的线性Transformer，降低二次复杂度
4. [HKVLM: Faithful Reasoning Grounding by Binding Language Queries to a Frozen Detector](/202606/30/2606.28862v1-hkvlm-faithful-reasoning-grounding-by-binding-language-queries-to-a-frozen-detector)  
   标签：评分：8.0/10、query:multimodal
   evidence：解决视觉语言模型中的幻觉和绑定失败，实现忠实推理
5. [ATMA: Length-Invariant Language Modeling via Polar Attention and Gated-Delta Compression Memory](/202606/30/2606.25156v2-atma-length-invariant-language-modeling-via-polar-attention-and-gated-delta-compression-memory)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：引入门控增量压缩记忆用于KV缓存压缩和长上下文建模
6. [Prism Transformer: Progressive Head Schedules for Hierarchical Attention Processing](/202606/30/2606.27449v1-prism-transformer-progressive-head-schedules-for-hierarchical-attention-processing)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：渐进式头部调度实现层级注意力处理，克服均匀头部分配瓶颈
7. [TAP-VLA: Tactile Annotation Prompting for Vision Language Action Models](/202606/30/2606.29089v1-tap-vla-tactile-annotation-prompting-for-vision-language-action-models)  
   标签：评分：7.0/10、query:multimodal
   evidence：将触觉反馈集成到VLA模型中以增强多模态理解
8. [Event-VLA: Action-Conditioned Event Fusion for Robust Vision-Language-Action Model](/202606/30/2606.29384v1-event-vla-action-conditioned-event-fusion-for-robust-vision-language-action-model)  
   标签：评分：7.0/10、query:multimodal
   evidence：多模态VLA模型，在变化光照下实现鲁棒操作
9. [Compression and Retrieval: Implicit Memory Retrieval for Video World Models](/202606/30/2606.23105v1-compression-and-retrieval-implicit-memory-retrieval-for-video-world-models)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：注意力驱动的记忆压缩与检索，用于高效处理扩展上下文
10. [Invoice Haystack: Benchmarking Document Retrieval and Visual Question Answering Under Strong Visual Homogeneity](/202606/30/2606.25343v2-invoice-haystack-benchmarking-document-retrieval-and-visual-question-answering-under-strong-visual-homogeneity)  
   标签：评分：6.0/10、query:multimodal
   evidence：针对视觉同质性下的多模态文档检索和VQA基准
11. [Multimodal Graph RAG for Long-range Visually Rich Document Understanding](/202606/30/2606.28780v1-multimodal-graph-rag-for-long-range-visually-rich-document-understanding)  
   标签：评分：6.0/10、query:multimodal
   evidence：多模态图RAG用于长文档理解
12. [Low-cost concept-based localized explanations: How far can we get with training-free approaches?](/202606/30/2606.29069v1-low-cost-concept-based-localized-explanations-how-far-can-we-get-with-training-free-approaches)  
   标签：评分：6.0/10、query:multimodal
   evidence：评估MLLM在局部概念命名上的能力，与多模态理解相关


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
