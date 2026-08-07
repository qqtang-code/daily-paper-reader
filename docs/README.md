<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-07
- 运行时间：2026-08-07 19:53:15 UTC
- 运行状态：成功
- 本次总论文数：11
- 精读区：6
- 速读区：5

### 今日简报（AI）
今日精读聚焦注意力加速与KV缓存压缩，11篇推送中6篇精读、5篇速读。最值得关注的是无训练哈希注意力和INT2缓存量化旋转法，均获9分以上高分。建议优先精读这两篇，再以速读方式浏览多模态嵌入与循环记忆新思路。
- 详情：[/202608/07/README](/202608/07/README)

### 精读区论文标签
1. [Training-Free Hashing-Based Attention via Binary Principal Components](/202608/07/2608.04405v1-training-free-hashing-based-attention-via-binary-principal-components)  
   标签：评分：10.0/10、query:sparse-attn
   evidence：面向长上下文LLM的无训练哈希稀疏注意力，直接解决稀疏注意力和KV缓存效率问题。
2. [Output-Aware Rotation for INT2 KV-Cache Quantization](/202608/07/2608.02691v2-output-aware-rotation-for-int2-kv-cache-quantization)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：提出OptR，一种输出感知的INT2 KV缓存量化旋转方法
3. [SAKI: Score-Aware Low-Rank Key Indexing with Random-Matrix Noise Correction for KV Retrieval](/202608/07/2608.03228v2-saki-score-aware-low-rank-key-indexing-with-random-matrix-noise-correction-for-kv-retrieval)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：低秩KV缓存，注意力分数感知索引，免训练
4. [Heterogeneous LLM Serving with General-Purpose Processing-Near-Memory for Retrieval-Based Sparse Attention](/202608/07/2608.03555v1-heterogeneous-llm-serving-with-general-purpose-processing-near-memory-for-retrieval-based-sparse-attention)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：专门面向检索式稀疏注意力的KV缓存卸载与近内存加速服务系统
5. [Spend Bits Where Queries Look: KV Cache Vector Quantization with Attention-Preserving Transforms](/202608/07/2608.04074v1-spend-bits-where-queries-look-kv-cache-vector-quantization-with-attention-preserving-transforms)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：用注意力保持变换进行KV缓存向量量化，在固定位数下减小缓存大小
6. [QEvict: Recoverable Quantized KV Eviction for Attention-Drift-Robust Long-Context Decoding](/202608/07/2608.05326v1-qevict-recoverable-quantized-kv-eviction-for-attention-drift-robust-long-context-decoding)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向长上下文解码的可恢复量化KV逐出方法，直接针对KV缓存压缩并关注注意力漂移鲁棒性。

### 速读区论文标签
1. [UEmbed: Unified Sparse and Dense Multimodal Embeddings](/202608/07/2608.02583v1-uembed-unified-sparse-and-dense-multimodal-embeddings)  
   标签：评分：8.0/10、query:multimodal
   evidence：统一稀疏与稠密多模态嵌入用于多模态检索
2. [Maglev: Sliding Recurrent Memory](/202608/07/2608.02870v2-maglev-sliding-recurrent-memory)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：滑动窗口注意力，循环记忆，固定大小记忆
3. [Fewer Tokens, Smaller Cache: Reward-Coordinated Efficient Reasoning](/202608/07/2608.04771v1-fewer-tokens-smaller-cache-reward-coordinated-efficient-reasoning)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：KV缓存压缩，推理模型，奖励协调
4. [Bole: Efficient Tree Speculation for Hybrid-Attention Language Models](/202608/07/2608.01651v1-bole-efficient-tree-speculation-for-hybrid-attention-language-models)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：混合注意力大模型的高效解码与KV缓存优化
5. [Mamba with Hierarchical Memory: Solving Representation Bottleneck in Long Sequence Modeling](/202608/07/2608.02347v2-mamba-with-hierarchical-memory-solving-representation-bottleneck-in-long-sequence-modeling)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：分层记忆克服长序列递归线性注意力模型的表示瓶颈


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
