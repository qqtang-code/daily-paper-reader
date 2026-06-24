<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-24
- 运行时间：2026-06-24 22:02:53 UTC
- 运行状态：成功
- 本次总论文数：19
- 精读区：7
- 速读区：12

### 今日简报（AI）
今日处理19篇论文，精读7篇，重点关注两项高分KV-Cache优化工作。 最值得看的两项9分研究：固定预算下KV-Cache流式淘汰策略（Nexus Sampling）与基于RoPE的位宽分配量化方法。 建议从这里入手，快速掌握LLM推理效率提升的关键技术。
- 详情：[/202606/24/README](/202606/24/README)

### 精读区论文标签
1. [Forget Without Compromise: Nexus Sampling for Streaming KV-Cache Eviction Under Fixed Budgets](/202606/24/2606.23961v1-forget-without-compromise-nexus-sampling-for-streaming-kv-cache-eviction-under-fixed-budgets)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：提出Nexus采样用于固定预算下的流式KV缓存驱逐
2. [RoPE-Aware Bit Allocation for KV-Cache Quantization](/202606/24/2606.24033v1-rope-aware-bit-allocation-for-kv-cache-quantization)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于RoPE的KV缓存量化比特分配
3. [CompressKV: Semantic-Retrieval-Guided KV-Cache Compression for Resource-Efficient Long-Context LLM Inference](/202606/24/2606.24467v1-compresskv-semantic-retrieval-guided-kv-cache-compression-for-resource-efficient-long-context-llm-inference)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：语义检索引导的KV缓存压缩方法用于长上下文LLM
4. [MMGist: A Comprehensive Multimodal Benchmark for 2027](/202606/24/2606.22437v1-mmgist-a-comprehensive-multimodal-benchmark-for-2027)  
   标签：评分：8.0/10、query:multimodal
   evidence：覆盖七个能力维度的多模态基准用于LVLM评估
5. [Look Light, Think Heavy: What Multimodal Chain-of-Thought Reasoning Can and Cannot Do](/202606/24/2606.22565v1-look-light-think-heavy-what-multimodal-chain-of-thought-reasoning-can-and-cannot-do)  
   标签：评分：8.0/10、query:mm-cot
   evidence：多模态思维链推理的系统性评估
6. [Faithful Grounded Visual Reasoning via Learned Proxy-Tokens](/202606/24/2606.23354v1-faithful-grounded-visual-reasoning-via-learned-proxy-tokens)  
   标签：评分：8.0/10、query:multimodal
   evidence：多模态幻觉检测通过视觉基础
7. [Listening makes Vision Clear for VLMs](/202606/24/2606.23763v1-listening-makes-vision-clear-for-vlms)  
   标签：评分：8.0/10、query:multimodal
   evidence：检测VLM中视觉注意力不一致性用于幻觉评估

### 速读区论文标签
1. [Grouped Query Experts: Mixture-of-Experts on GQA Self-Attention](/202606/24/2606.20945v2-grouped-query-experts-mixture-of-experts-on-gqa-self-attention)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：在分组查询注意力上应用混合专家层以减少计算并保持KV缓存优势
2. [Mind the Heads: Topological Representation Alignment for Multimodal LLMs](/202606/24/2606.23885v1-mind-the-heads-topological-representation-alignment-for-multimodal-llms)  
   标签：评分：8.0/10、query:multimodal
   evidence：多头表示对齐用于多模态大模型
3. [Accelerating Multimodal Large Language Models with Prior-Corrected Token Reduction](/202606/24/2606.24156v1-accelerating-multimodal-large-language-models-with-prior-corrected-token-reduction)  
   标签：评分：8.0/10、query:multimodal
   evidence：通过先验校正注意力加速多模态大模型的token缩减方法
4. [Latent Visual States for Efficient Multimodal Reasoning](/202606/24/2606.24233v1-latent-visual-states-for-efficient-multimodal-reasoning)  
   标签：评分：8.0/10、query:multimodal
   evidence：高效多模态推理框架，使用潜在视觉状态
5. [TuringViT: Making SOTA Vision Transformers Accessible to All](/202606/24/2606.24253v1-turingvit-making-sota-vision-transformers-accessible-to-all)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：视觉Transformer的高效线性注意力
6. [4DVLT: Dynamic Scene Understanding with Worldline-Centered Vision-Language Tracking](/202606/24/2606.22631v1-4dvlt-dynamic-scene-understanding-with-worldline-centered-vision-language-tracking)  
   标签：评分：7.0/10、query:multimodal
   evidence：以世界线为中心的视觉语言跟踪，用于4D动态场景理解
7. [Attention-Spectrum Regularization for Replay-Free Continual Multimodal LLMs](/202606/24/2606.23063v1-attention-spectrum-regularization-for-replay-free-continual-multimodal-llms)  
   标签：评分：7.0/10、query:multimodal
   evidence：注意力谱正则化用于持续多模态大模型
8. [HANCLIP: A Family of Hyperbolic Angular Negation Vision Language Models](/202606/24/2606.23843v1-hanclip-a-family-of-hyperbolic-angular-negation-vision-language-models)  
   标签：评分：7.0/10、query:multimodal
   evidence：视觉语言模型处理否定脆弱性
9. [MedBench v5: A Dynamic, Process-Oriented, and Hallucination-Aware Benchmark for Clinical Multimodal Models](/202606/24/2606.24155v1-medbench-v5-a-dynamic-process-oriented-and-hallucination-aware-benchmark-for-clinical-multimodal-models)  
   标签：评分：7.0/10、query:multimodal
   evidence：面向临床多模态模型的基准，包含幻觉检测
10. [Scalable Hierarchical Attention Transformers for Multi-Turn Jailbreak Detection in Long Conversations](/202606/24/2606.21082v1-scalable-hierarchical-attention-transformers-for-multi-turn-jailbreak-detection-in-long-conversations)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：高效层次化注意力避免长上下文拼接
11. [Compression and Retrieval: Implicit Memory Retrieval for Video World Models](/202606/24/2606.23105v1-compression-and-retrieval-implicit-memory-retrieval-for-video-world-models)  
   标签：评分：6.0/10、query:multimodal
   evidence：视频世界模型的隐式记忆检索，与多模态理解相关
12. [VSANet: View-aware Sparse Attention Network for Light Field Image Denoising](/202606/24/2606.24737v1-vsanet-view-aware-sparse-attention-network-for-light-field-image-denoising)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：稀疏注意力用于光场去噪


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
