<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-28
- 运行时间：2026-07-28 20:24:07 UTC
- 运行状态：成功
- 本次总论文数：16
- 精读区：6
- 速读区：10

### 今日简报（AI）
1) 今日重点解析注意力机制优化与模型压缩，精读两篇高分论文（10分&9分），速读三篇压缩相关研究（8分）。
2) 最值得关注：PIVOT的令牌级稀疏注意力索引方案，以及多头潜在注意力分离内容与位置的新发现。
3) 建议跟进这些高效注意力与压缩方法在边缘智能和多模态大模型中的落地验证。
- 详情：[/202607/28/README](/202607/28/README)

### 精读区论文标签
1. [PIVOT: Efficient Query-Group Indexing for Token-Level Sparse Attention](/202607/28/2607.24593v1-pivot-efficient-query-group-indexing-for-token-level-sparse-attention)  
   标签：评分：10.0/10、query:sparse-attn
   evidence：令牌级稀疏注意力索引，提高注意力效率
2. [Through the Bottleneck: How Multi-head Latent Attention Separates Content from Position in Language Models](/202607/28/2607.23054v1-through-the-bottleneck-how-multi-head-latent-attention-separates-content-from-position-in-language-models)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：多头潜在注意力实现KV缓存压缩
3. [Sol-Attn: Accelerating Video Generation Inference via On-the-Fly Attention Sparsification](/202607/28/2607.24027v1-sol-attn-accelerating-video-generation-inference-via-on-the-fly-attention-sparsification)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向视频生成的即时注意力稀疏化
4. [DynaCalKV: Key-Value Cache Compression via Head Grouping and Adaptive Rank Allocation](/202607/28/2607.24331v1-dynacalkv-key-value-cache-compression-via-head-grouping-and-adaptive-rank-allocation)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：通过头分组和自适应秩分配的低秩KV缓存压缩
5. [LOCKS: Page-Local Compact Key Summaries for Efficient Long-Context Decoding](/202607/28/2607.24555v1-locks-page-local-compact-key-summaries-for-efficient-long-context-decoding)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于页级谱摘要的KV缓存压缩
6. [Eviction as Estimation: A Fixed-Lag Smoothing View of Test-Time Memory, and When Measuring Beats Accumulating](/202607/28/2607.24667v1-eviction-as-estimation-a-fixed-lag-smoothing-view-of-test-time-memory-and-when-measuring-beats-accumulating)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：LLM工作记忆的驱逐策略，KV缓存压缩

### 速读区论文标签
1. [Beyond Independent Optimization: Compression, MoE Routing, and Quantization Interactions in Multimodal Edge Intelligence](/202607/28/2607.20981v1-beyond-independent-optimization-compression-moe-routing-and-quantization-interactions-in-multimodal-edge-intelligence)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：综述覆盖KV缓存优化和令牌压缩
2. [Structured Redundancy Modeling for Efficient Visual Token Pruning in High-Resolution MLLMs](/202607/28/2607.23046v1-structured-redundancy-modeling-for-efficient-visual-token-pruning-in-high-resolution-mllms)  
   标签：评分：8.0/10、query:multimodal
   evidence：面向高分辨率多模态大模型的视觉令牌剪枝
3. [OmniScope: Modality-Decoupled Token Compression for Omnimodal Large Language Models](/202607/28/2607.23193v1-omniscope-modality-decoupled-token-compression-for-omnimodal-large-language-models)  
   标签：评分：8.0/10、query:multimodal
   evidence：多模态大模型的解耦式令牌压缩
4. [Disentangling Semantic Attention from Structural Bias in the Attention Manifold](/202607/28/2607.24017v1-disentangling-semantic-attention-from-structural-bias-in-the-attention-manifold)  
   标签：评分：8.0/10、query:multimodal
   evidence：多模态大模型注意力分析，处理视觉注意力沉没与幻觉
5. [Omni-Prune: Query-Aware Unified Token Pruning for Efficient Omnimodal Large Language Models](/202607/28/2607.23445v1-omni-prune-query-aware-unified-token-pruning-for-efficient-omnimodal-large-language-models)  
   标签：评分：7.0/10、query:multimodal
   evidence：针对高效多模态大模型的查询感知Token剪枝
6. [RED-PIM: Reducing Data Movement for Transformers using Processing-in-Memory](/202607/28/2607.21731v1-red-pim-reducing-data-movement-for-transformers-using-processing-in-memory)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：基于处理内存的Transformer注意力硬件加速
7. [What Softmax Throws Away: Mass-Aware Attention for Evidence Accumulation](/202607/28/2607.22781v1-what-softmax-throws-away-mass-aware-attention-for-evidence-accumulation)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：改进注意力机制以更好累积证据
8. [Libra: Taming Attention Workload Skew in Long-Context LLM Training with Bounded Sequence Pool](/202607/28/2607.23250v1-libra-taming-attention-workload-skew-in-long-context-llm-training-with-bounded-sequence-pool)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：长上下文大语言模型训练中的注意力负载均衡
9. [A Coulomb Particle Model for Learning Kernel Attention in Transformers](/202607/28/2607.23869v1-a-coulomb-particle-model-for-learning-kernel-attention-in-transformers)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：学习随机特征实现线性化Transformer注意力
10. [MXAttention: Data-Free Optimal Scaling and Pre-Normalization Quantization for MXFP4 Attention](/202607/28/2607.24377v1-mxattention-data-free-optimal-scaling-and-pre-normalization-quantization-for-mxfp4-attention)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：针对高效注意力的数据无关量化


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
