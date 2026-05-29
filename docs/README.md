<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-05-20 ~ 2026-05-29
- 运行时间：2026-05-29 13:37:08 UTC
- 运行状态：成功
- 本次总论文数：35
- 精读区：24
- 速读区：11

### 今日简报（AI）
2026年5月20-29日精选35篇论文，聚焦稀疏注意力机制优化，多篇提出免训练或低秩加速方案。  
最值得关注方向：通用Top-k稀疏注意力实现无训练高效推理与稀疏感知训练（UNIQUE，10分）；3D RoPE驱动的稀疏低秩注意力显著提升扩散变换器效率（RoPeSLR，9分）。  
建议尝试将UNIQUE的稀疏策略迁移至现有模型，或结合RoPeSLR的空间旋转位置编码加速图像生成任务。
- 详情：[/20260520-20260529/README](/20260520-20260529/README)

### 精读区论文标签
1. [UNIQUE: Universal Top-k Sparse Attention for Training-free Inference and Sparsity-aware Training](/20260520-20260529/2605.27740v1-unique-universal-top-k-sparse-attention-for-training-free-inference-and-sparsity-aware-training)  
   标签：评分：10.0/10、query:sparse-attn
   evidence：通用top-k稀疏注意力框架，同时支持推理和训练
2. [RoPeSLR: 3D RoPE-driven Sparse-LowRank Attention for Efficient Diffusion Transformers](/20260520-20260529/2605.20659v1-ropeslr-3d-rope-driven-sparse-lowrank-attention-for-efficient-diffusion-transformers)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：稀疏低秩注意力
3. [LT2: Linear-Time Looped Transformers](/20260520-20260529/2605.20670v1-lt2-linear-time-looped-transformers)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：在循环Transformer中用线性或稀疏注意力替代二次注意力
4. [LT2: Linear-Time Looped Transformers](/20260520-20260529/2605.20670v2-lt2-linear-time-looped-transformers)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：在循环Transformer中用线性或稀疏注意力替代二次注意力
5. [Runtime-Certified Bounded-Error Quantized Attention](/20260520-20260529/2605.20868v1-runtime-certified-bounded-error-quantized-attention)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：KV缓存量化与运行时认证，用于大模型推理
6. [OCTOPUS: Optimized KV Cache for Transformers via Octahedral Parametrization Under optimal Squared error quantization](/20260520-20260529/2605.21226v1-octopus-optimized-kv-cache-for-transformers-via-octahedral-parametrization-under-optimal-squared-error-quantization)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：通过八面体参数化和联合量化进行KV缓存压缩
7. [EntmaxKV: Support-Aware Decoding for Entmax Attention](/20260520-20260529/2605.21649v1-entmaxkv-support-aware-decoding-for-entmax-attention)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：利用entmax注意力实现精确支持恢复的稀疏解码与KV缓存减少
8. [MuKV: Multi-Grained KV Cache Compression for Long Streaming Video Question-Answering](/20260520-20260529/2605.22269v1-mukv-multi-grained-kv-cache-compression-for-long-streaming-video-question-answering)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：提出多粒度KV缓存压缩方法
9. [Meta-Soft: Leveraging Composable Meta-Tokens for Context-Preserving KV Cache Compression](/20260520-20260529/2605.22337v1-meta-soft-leveraging-composable-meta-tokens-for-context-preserving-kv-cache-compression)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：KV缓存压缩，动态压缩
10. [Meta-Soft: Leveraging Composable Meta-Tokens for Context-Preserving KV Cache Compression](/20260520-20260529/2605.22337v2-meta-soft-leveraging-composable-meta-tokens-for-context-preserving-kv-cache-compression)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：动态元标记的KV缓存压缩
11. [Structured-Sparse Attention for Entity Tracking with Subquadratic Sequence Complexity](/20260520-20260529/2605.22476v1-structured-sparse-attention-for-entity-tracking-with-subquadratic-sequence-complexity)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：结构化稀疏注意力且复杂度低于二次
12. [ThriftAttention: Selective Mixed Precision for Long-Context FP4 Attention](/20260520-20260529/2605.23081v1-thriftattention-selective-mixed-precision-for-long-context-fp4-attention)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：选择性混合精度实现长上下文注意力
13. [Adaptive Mass-Segmented KV Compression for Long-Context Reasoning](/20260520-20260529/2605.23200v1-adaptive-mass-segmented-kv-compression-for-long-context-reasoning)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：KV压缩，长上下文推理
14. [A Simple Plug-in for Improving Eviction-Based KV Cache Compression](/20260520-20260529/2605.23258v1-a-simple-plug-in-for-improving-eviction-based-kv-cache-compression)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于驱逐的KV缓存压缩的即插即用改进，引入三路路由
15. [DFSAttn: Dynamic Fine-grained Sparse Attention for Efficient Video Generation](/20260520-20260529/2605.23445v1-dfsattn-dynamic-fine-grained-sparse-attention-for-efficient-video-generation)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：动态细粒度稀疏注意力
16. [Adaptive KV Cache Reuse for Fast Long-Context LLM Serving](/20260520-20260529/2605.24022v1-adaptive-kv-cache-reuse-for-fast-long-context-llm-serving)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：针对非前缀场景的自适应KV缓存重用
17. [Inference Time Context Sparsity: Illusion or Opportunity?](/20260520-20260529/2605.24168v1-inference-time-context-sparsity-illusion-or-opportunity)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：主张在LLM推理中采用极端上下文稀疏性
18. [Grammatically-Guided Sparse Attention for Efficient and Interpretable Transformers](/20260520-20260529/2605.24518v1-grammatically-guided-sparse-attention-for-efficient-and-interpretable-transformers)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于词性标注的语法引导稀疏注意力
19. [CONF-KV: Confidence-Aware KV Cache Eviction with Mixed-Precision Storage for Long-Horizon LLM](/20260520-20260529/2605.24786v1-conf-kv-confidence-aware-kv-cache-eviction-with-mixed-precision-storage-for-long-horizon-llm)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于置信度的KV缓存驱逐与混合精度存储
20. [Polynomial Context-Truncation Sensitivity in Autoregressive Language Models: Sequential Wyner-Ziv Bounds for KV Cache Compression](/20260520-20260529/2605.25085v1-polynomial-context-truncation-sensitivity-in-autoregressive-language-models-sequential-wyner-ziv-bounds-for-kv-cache-compression)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：KV缓存压缩的率失真界限与多项式衰减理论
21. [NestedKV: Nested Memory Routing for Long-Context KV Cache Compression](/20260520-20260529/2605.26678v1-nestedkv-nested-memory-routing-for-long-context-kv-cache-compression)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：多尺度仅键的KV缓存压缩方法用于长上下文大模型
22. [Hurwitz Quaternion Multiplicative Quantization for KV Cache Compression](/20260520-20260529/2605.27646v1-hurwitz-quaternion-multiplicative-quantization-for-kv-cache-compression)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：KV缓存压缩量化
23. [Augmenting Attention with Exponentially Decaying Memory Improves Query-Aware KV Sparsity](/20260520-20260529/2605.28640v1-augmenting-attention-with-exponentially-decaying-memory-improves-query-aware-kv-sparsity)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：指数衰减记忆提升查询感知的KV稀疏性
24. [OSP-Next: Efficient High-Quality Video Generation with Sparse Sequence Parallelism, HiF8 Quantization, and Reinforcement Learning](/20260520-20260529/2605.28691v1-osp-next-efficient-high-quality-video-generation-with-sparse-sequence-parallelism-hif8-quantization-and-reinforcement-learning)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：稀疏注意力机制

### 速读区论文标签
1. [PulseCol: Periodically Refreshed Column-Sparse Attention for Accelerating Diffusion Language Models](/20260520-20260529/2605.20813v1-pulsecol-periodically-refreshed-column-sparse-attention-for-accelerating-diffusion-language-models)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：周期性刷新的列稀疏注意力用于扩散语言模型
2. [WorldKV: Efficient World Memory with World Retrieval and Compression](/20260520-20260529/2605.22718v1-worldkv-efficient-world-memory-with-world-retrieval-and-compression)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：KV缓存压缩与检索
3. [Gated DeltaNet-2: Decoupling Erase and Write in Linear Attention](/20260520-20260529/2605.22791v1-gated-deltanet-2-decoupling-erase-and-write-in-linear-attention)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：解耦线性注意力中的擦除与写入实现高效记忆
4. [Tensor Cache: Eviction-conditioned Associative Memory for Transformers](/20260520-20260529/2605.22884v1-tensor-cache-eviction-conditioned-associative-memory-for-transformers)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：基于淘汰条件联想记忆的两级缓存实现KV压缩
5. [Head-Aware Key-Value Compression for Efficient Autoregressive Image Generation](/20260520-20260529/2605.20600v1-head-aware-key-value-compression-for-efficient-autoregressive-image-generation)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：头部感知KV压缩，技术可迁移到大语言模型
6. [NanoCP: Request-Level Dynamic Context Parallelism for Data-Expert Parallel Decoding](/20260520-20260529/2605.21100v1-nanocp-request-level-dynamic-context-parallelism-for-data-expert-parallel-decoding)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：面向MoE模型的动态上下文并行，处理注意力延迟与KV缓存碎片化
7. [Quantized Keys Steal Attention: Bias Correction for KV-Cache Compression in Video Diffusion](/20260520-20260529/2605.26266v1-quantized-keys-steal-attention-bias-correction-for-kv-cache-compression-in-video-diffusion)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：视频扩散模型中KV缓存量化的偏差校正
8. [CIVIC: End-to-End Sequence Compactness for Efficient Vision-Language Models](/20260520-20260529/2605.28115v1-civic-end-to-end-sequence-compactness-for-efficient-vision-language-models)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：视觉语言模型中通过紧凑序列表示的KV缓存压缩
9. [Layer-wise Token Compression for Efficient Document Reranking](/20260520-20260529/2605.20683v2-layer-wise-token-compression-for-efficient-document-reranking)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：逐层令牌压缩用于高效重排序
10. [ArborKV: Structure-Aware KV Cache Management for Scaling Tree-based LLM Reasoning](/20260520-20260529/2605.22106v1-arborkv-structure-aware-kv-cache-management-for-scaling-tree-based-llm-reasoning)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：面向树形LLM推理的结构感知KV缓存管理
11. [ASAP: Attention Sink Anchored Pruning](/20260520-20260529/2605.22372v1-asap-attention-sink-anchored-pruning)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：面向视觉Transformer的注意力汇点锚定剪枝


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
