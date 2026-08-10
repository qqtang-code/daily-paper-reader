<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-10
- 运行时间：2026-08-10 19:52:58 UTC
- 运行状态：成功
- 本次总论文数：11
- 精读区：6
- 速读区：5

### 今日简报（AI）
今日聚焦KV Cache压缩与稀疏注意力，兼及多模态视觉Token剪枝，共解读11篇论文。  
最值得关注两篇9分工作：从冻结Query-Key几何实现无数据稀疏注意力，以及全局分配KV Cache分辨率与覆盖度。  
建议优先精读这两篇高分论文，再对比速读中的视觉Token剪枝方法，理解不同压缩策略的取舍。
- 详情：[/202608/10/README](/202608/10/README)

### 精读区论文标签
1. [Autonomy-of-Heads: Data-Free Sparse Attention from Frozen Query-Key Geometry](/202608/10/2608.06849v1-autonomy-of-heads-data-free-sparse-attention-from-frozen-query-key-geometry)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于查询-键谱几何识别检索头与流式头的无数据稀疏注意力和KV压缩
2. [Every Cache Entry Earns Its Place: Global Allocation of Resolution and Coverage for KV Cache Compression](/202608/10/2608.07001v1-every-cache-entry-earns-its-place-global-allocation-of-resolution-and-coverage-for-kv-cache-compression)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向KV缓存压缩的全局资源分配方法，跨层、头、槽联合优化分辨率与覆盖率
3. [HiSparse: Scaling Sparse-Attention Decoding with Hierarchical KV Cache Management](/202608/10/2608.07009v1-hisparse-scaling-sparse-attention-decoding-with-hierarchical-kv-cache-management)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向Top-k稀疏注意力服务的层级KV缓存管理，将完整KV保留在宿主内存并以小GPU缓存限定解码占用
4. [CoinRAG: Contextualized Information Nugget KV Cache Reuse for Long-Context RAG](/202608/10/2608.07458v1-coinrag-contextualized-information-nugget-kv-cache-reuse-for-long-context-rag)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：针对长上下文RAG的KV缓存复用，减少冗余上下文处理
5. [Does Accuracy Equal Evidence? Reasoning Faithfulness under KV Cache Compression](/202608/10/2608.01631v1-does-accuracy-equal-evidence-reasoning-faithfulness-under-kv-cache-compression)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：研究KV缓存压缩对推理忠实度的影响
6. [Runtime Observability for Heterogeneous Attention Memory](/202608/10/2608.05863v1-runtime-observability-for-heterogeneous-attention-memory)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：为异构注意力记忆（潜变量缓存、稀疏选择器、循环状态）提供运行时观测契约，组合误差上界以管理压缩风险

### 速读区论文标签
1. [Learning to Predict Middle-Layer Attention in MLLMs for Visual Token Prunin](/202608/10/2608.06411v1-learning-to-predict-middle-layer-attention-in-mllms-for-visual-token-prunin)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：基于预测中间层注意力的多模态视觉token剪枝
2. [Retrofitting Linear Attention into Diffusion Language Models](/202608/10/2608.06628v1-retrofitting-linear-attention-into-diffusion-language-models)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：块混合注意力在扩散语言模型中线性化前缀注意力，降低重复前缀开销
3. [RoRA: Role-Oriented Regional Allocation for Visual Token Pruning in MLLMs](/202608/10/2608.07088v1-rora-role-oriented-regional-allocation-for-visual-token-pruning-in-mllms)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：面向多模态大模型的免训练视觉令牌剪枝，降低KV缓存存储
4. [Addressable Memory for Video World Models](/202608/10/2608.07408v1-addressable-memory-for-video-world-models)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：面向视频世界模型的无训练KV缓存压缩与地址保持框架
5. [CoDAT: Collaborative Dual-Attention Transformer with Low-Cost Temporal Modeling for Efficient Edge Action Recognition](/202608/10/2608.06691v1-codat-collaborative-dual-attention-transformer-with-low-cost-temporal-modeling-for-efficient-edge-action-recognition)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：通过协作双分支注意力模块压缩Q/K/V，是一种面向Transformer的高效注意力机制


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
