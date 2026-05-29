<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-05-29
- 运行时间：2026-05-29 21:51:44 UTC
- 运行状态：成功
- 本次总论文数：17
- 精读区：6
- 速读区：11

### 今日简报（AI）
今日推荐17篇论文，精读6篇，其中《Interdomain Attention》与《IndexMem》均获9.0满分，聚焦长上下文LLM推理的注意力与缓存革新。值得关注的两大方向：跨域注意力超越Token级记忆，以及学习型KV缓存淘汰结合潜在记忆，均旨在突破长序列效率瓶颈。建议优先精读这两篇9.0分论文，掌握如何通过结构化缓存与层级注意力降低长上下文推理成本。
- 详情：[/202605/29/README](/202605/29/README)

### 精读区论文标签
1. [Interdomain Attention: Beyond Token-Level Key-Value Memory](/202605/29/2605.24330v1-interdomain-attention-beyond-token-level-key-value-memory)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：将SSM集成到注意力模块实现固定大小压缩KV状态
2. [IndexMem: Learned KV-Cache Eviction with Latent Memory for Long-Context LLM Inference](/202605/29/2605.25475v1-indexmem-learned-kv-cache-eviction-with-latent-memory-for-long-context-llm-inference)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向长上下文LLM的可学习KV缓存淘汰策略
3. [Moment-KV: Momentum-Based Decode-Time KV Cache Compression for Long Generation](/202605/29/2605.29873v1-moment-kv-momentum-based-decode-time-kv-cache-compression-for-long-generation)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于动量的解码阶段KV缓存压缩，利用注意力动态
4. [Veda: Scalable Video Diffusion via Distilled Sparse Attention](/202605/29/2605.30325v1-veda-scalable-video-diffusion-via-distilled-sparse-attention)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：蒸馏稀疏注意力用于视频扩散
5. [Energy-Gated Attention: Spectral Salience as an Inductive Bias for Transformer Attention](/202605/29/2605.21842v1-energy-gated-attention-spectral-salience-as-an-inductive-bias-for-transformer-attention)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：提出能量门控注意力聚焦信息丰富token以减少计算
6. [Inference Time Context Sparsity: Illusion or Opportunity?](/202605/29/2605.24168v1-inference-time-context-sparsity-illusion-or-opportunity)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：立场论文倡导极端上下文稀疏性

### 速读区论文标签
1. [ArborKV: Structure-Aware KV Cache Management for Scaling Tree-based LLM Reasoning](/202605/29/2605.22106v1-arborkv-structure-aware-kv-cache-management-for-scaling-tree-based-llm-reasoning)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：面向树结构推理的KV缓存管理
2. [Meta-Attention: Bayesian Per-Token Routing for Efficient Transformer Inference](/202605/29/2605.28384v1-meta-attention-bayesian-per-token-routing-for-efficient-transformer-inference)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：动态路由选择稀疏注意力策略
3. [Parallax: Parameterized Local Linear Attention for Language Modeling](/202605/29/2605.29157v1-parallax-parameterized-local-linear-attention-for-language-modeling)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：参数化局部线性注意力用于高效语言建模
4. [VideoMLA: Low-Rank Latent KV Cache for Minute-Scale Autoregressive Video Diffusion](/202605/29/2605.30351v1-videomla-low-rank-latent-kv-cache-for-minute-scale-autoregressive-video-diffusion)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：低秩潜在KV缓存用于视频扩散
5. [Approaching I/O-optimality for Approximate Attention](/202605/29/2605.23751v1-approaching-io-optimality-for-approximate-attention)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：近似注意力的I/O最优，近线性代价
6. [Language Models Need Sleep](/202605/29/2605.26099v1-language-models-need-sleep)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：通过快速权重整合清除键值缓存
7. [Energy-Gated Attention and Wavelet Positional Encoding: Complementary Inductive Biases for Transformer Attention](/202605/29/2605.26355v1-energy-gated-attention-and-wavelet-positional-encoding-complementary-inductive-biases-for-transformer-attention)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：能量门控注意力实现高效Transformer注意力
8. [JetViT: Efficient High-Resolution Vision Transformer with Post-Training Attention Search](/202605/29/2605.26636v1-jetvit-efficient-high-resolution-vision-transformer-with-post-training-attention-search)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：训练后搜索将注意力替换为高效变体
9. [Preisach Attention: A Hysteretic Model of Sequential Memory](/202605/29/2605.23603v1-preisach-attention-a-hysteretic-model-of-sequential-memory)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：替代softmax的新型注意力机制
10. [A generative pre-trained transformer with Kerr-soliton attention](/202605/29/2605.24124v1-a-generative-pre-trained-transformer-with-kerr-soliton-attention)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：新型硬件高效注意力机制
11. [Quaternion Self-Attention with Shared Scores](/202605/29/2605.24920v1-quaternion-self-attention-with-shared-scores)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：基于共享分数的四元数自注意力高效计算


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
