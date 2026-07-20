<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-20
- 运行时间：2026-07-20 21:00:10 UTC
- 运行状态：成功
- 本次总论文数：11
- 精读区：6
- 速读区：5

### 今日简报（AI）
今日日报聚焦有限显存下的长上下文微调与KV缓存近无损压缩，同时涵盖视觉语言模型的轻量级token缩减与并行扩散优化。  
最值得精读的两篇：Long-Context Fine-Tuning with Limited VRAM（10分）和基于Joint Tucker与JL残差分配的KV缓存压缩方法（9分）。  
建议优先尝试高效微调与缓存压缩技术，再结合轻量级token减少方法提升VLM实际应用效率。
- 详情：[/202607/20/README](/202607/20/README)

### 精读区论文标签
1. [Long-Context Fine-Tuning with Limited VRAM](/202607/20/2607.15105v2-long-context-fine-tuning-with-limited-vram)  
   标签：评分：10.0/10、query:sparse-attn
   evidence：直接针对长上下文微调中的KV缓存压缩和稀疏注意力
2. [A JoLT for the KV Cache: Near-Lossless KV Cache Compression via Joint Tucker and JL-Residual Allocation for LLMs](/202607/20/2607.12550v2-a-jolt-for-the-kv-cache-near-lossless-kv-cache-compression-via-joint-tucker-and-jl-residual-allocation-for-llms)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：通过联合Tucker和JL残差分配进行KV缓存压缩
3. [Looped Latent Attention: Cross-Loop KV Compression for Looped Transformers](/202607/20/2607.15456v1-looped-latent-attention-cross-loop-kv-compression-for-looped-transformers)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：循环变压器的KV缓存压缩
4. [VarRate: Training-Free Variable-Rate KV Cache Compression for Long-Context LLMs](/202607/20/2607.15498v1-varrate-training-free-variable-rate-kv-cache-compression-for-long-context-llms)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：通过低秩分配实现可变速率KV缓存压缩
5. [FVAttn: Adaptive Sparse Attention with Runtime Load Balancing for Video Generation](/202607/20/2607.16190v1-fvattn-adaptive-sparse-attention-with-runtime-load-balancing-for-video-generation)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：用于视频生成的自适应稀疏注意力与负载均衡
6. [Efficient Frame Selection for Long Videos at Test Time with Attention-Based MLLM Selectors](/202607/20/2607.15689v1-efficient-frame-selection-for-long-videos-at-test-time-with-attention-based-mllm-selectors)  
   标签：评分：8.0/10、query:multimodal
   evidence：基于注意力的MLLM帧选择，与多模态理解相关

### 速读区论文标签
1. [Attention-Free and Lightweight Token Reduction for Efficient Vision-Language Models](/202607/20/2607.13500v1-attention-free-and-lightweight-token-reduction-for-efficient-vision-language-models)  
   标签：评分：7.0/10、query:multimodal
   evidence：无注意力令牌减少方法用于多模态理解
2. [T^2MLR: Transformer with Temporal Middle-Layer Recurrence](/202607/20/2607.15178v2-t2mlr-transformer-with-temporal-middle-layer-recurrence)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：基于缓存中间层表示的时间递归
3. [DiTango: Cost-Effective Parallel Diffusion Generation with Selective Attention State Reuse](/202607/20/2607.15650v1-ditango-cost-effective-parallel-diffusion-generation-with-selective-attention-state-reuse)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：扩散Transformer中的选择性注意力状态重用
4. [DSTAR: Accelerating Diffusion Transformers via Spatial and Temporal Redundancy Reduction](/202607/20/2607.15846v1-dstar-accelerating-diffusion-transformers-via-spatial-and-temporal-redundancy-reduction)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：通过时空冗余减少加速扩散Transformer
5. [PagedWeight: Efficient MoE LLM Serving with Dynamic Quality-Aware Weight Quantization](/202607/20/2607.16184v1-pagedweight-efficient-moe-llm-serving-with-dynamic-quality-aware-weight-quantization)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：MoE权重的动态量化与KV缓存内存平衡


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
