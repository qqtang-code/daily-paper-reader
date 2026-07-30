<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-30
- 运行时间：2026-07-30 21:08:29 UTC
- 运行状态：成功
- 本次总论文数：16
- 精读区：6
- 速读区：10

### 今日简报（AI）
今日聚焦注意力机制优化与稀疏记忆管理，精读两篇9分论文。最值得关注的是注意力流形中语义与结构偏差的解耦方法，以及全局计算结合局部物化的稀疏事件KV存储策略。建议普通读者优先阅读速读中的令牌剪枝与大模型记忆管理方案。
- 详情：[/202607/30/README](/202607/30/README)

### 精读区论文标签
1. [Compute Globally, Materialize Locally: The Memory Contract of Sparse Event-KV](/202607/30/2607.23693v1-compute-globally-materialize-locally-the-memory-contract-of-sparse-event-kv)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：长时程智能体中的KV缓存使用，稀疏事件KV记忆契约
2. [Disentangling Semantic Attention from Structural Bias in the Attention Manifold](/202607/30/2607.24017v1-disentangling-semantic-attention-from-structural-bias-in-the-attention-manifold)  
   标签：评分：9.0/10、query:multimodal
   evidence：多模态注意力偏差与视觉注意力汇点分析
3. [DualDecoder: Accelerate Long Context LLM Inference by Predictive Prefetch](/202607/30/2607.26475v1-dualdecoder-accelerate-long-context-llm-inference-by-predictive-prefetch)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：KV缓存压缩、稀疏KV缓存、长上下文LLM推理
4. [InferScale: GPU-Native KV Injection for Personalized LLM Serving](/202607/30/2607.27090v1-inferscale-gpu-native-kv-injection-for-personalized-llm-serving)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向LLM服务的GPU原生KV注入
5. [A Photonic-CXL Memory Appliance for Scalable KV Cache Management in LLM Inference](/202607/30/2607.27187v1-a-photonic-cxl-memory-appliance-for-scalable-kv-cache-management-in-llm-inference)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：直接针对大语言模型推理中的KV缓存管理问题，提出光子-CXL混合架构，实现可扩展的大容量共享内存
6. [OmniScope: Modality-Decoupled Token Compression for Omnimodal Large Language Models](/202607/30/2607.23193v2-omniscope-modality-decoupled-token-compression-for-omnimodal-large-language-models)  
   标签：评分：8.0/10、query:multimodal
   evidence：面向全模态大语言模型的模态解耦令牌压缩

### 速读区论文标签
1. [Omni-Prune: Query-Aware Unified Token Pruning for Efficient Omnimodal Large Language Models](/202607/30/2607.23445v1-omni-prune-query-aware-unified-token-pruning-for-efficient-omnimodal-large-language-models)  
   标签：评分：8.0/10、query:multimodal
   evidence：面向全模态LLM的查询感知令牌剪枝，减少多模态理解中的内存
2. [Variational-Ising-Attention (VIA):TailoredAttentionMattersfor Science](/202607/30/2607.23634v1-variational-ising-attention-viatailoredattentionmattersfor-science)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：提出基于伊辛模型的变分注意力机制，旨在实现稀疏和高效注意力，与稀疏注意力机制直接相关
3. [Memory for Large Language Models](/202607/30/2607.25380v1-memory-for-large-language-models)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：综述了大语言模型中的记忆机制，包括瞬态注意力和KV缓存等，与KV缓存优化相关
4. [Seen, Said, or Forgotten? A Causal Audit of Visual KV Memory Across Dialog Turns](/202607/30/2607.25467v1-seen-said-or-forgotten-a-causal-audit-of-visual-kv-memory-across-dialog-turns)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：跨对话轮次视觉KV内存驱逐的因果审计
5. [Structured Redundancy Modeling for Efficient Visual Token Pruning in High-Resolution MLLMs](/202607/30/2607.23046v1-structured-redundancy-modeling-for-efficient-visual-token-pruning-in-high-resolution-mllms)  
   标签：评分：7.0/10、query:multimodal
   evidence：面向高分辨率多模态大语言模型的结构化冗余建模视觉令牌剪枝
6. [OmniScope: Modality-Decoupled Token Compression for Omnimodal Large Language Models](/202607/30/2607.23193v1-omniscope-modality-decoupled-token-compression-for-omnimodal-large-language-models)  
   标签：评分：7.0/10、query:multimodal
   evidence：面向全模态大语言模型的模态解耦令牌压缩，以查询为锚点
7. [Kalypso: Relational LLM Serving](/202607/30/2607.23815v1-kalypso-relational-llm-serving)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：关系型LLM服务中通过流水线执行复用KV缓存
8. [OmniCache: Multidimensional Hierarchical Feature Caching For Diffusion Models](/202607/30/2607.23844v1-omnicache-multidimensional-hierarchical-feature-caching-for-diffusion-models)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：扩散模型的多维特征缓存
9. [Phase Structure in Rotary Attention: A Spectral Framework for Semantic Continuity and Execution-Boundary Governance](/202607/30/2607.25507v1-phase-structure-in-rotary-attention-a-spectral-framework-for-semantic-continuity-and-execution-boundary-governance)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：对Transformer注意力中旋转位置编码相位结构的频谱分析
10. [SepPrune:A Separator-based Pruning Framework for Efficient Multimodal Large Language Models](/202607/30/2607.25818v1-sepprunea-separator-based-pruning-framework-for-efficient-multimodal-large-language-models)  
   标签：评分：6.0/10、query:multimodal
   evidence：提出针对多模态大语言模型的视觉token剪枝方法，提升效率，属于多模态理解模型方向


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
