<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-11
- 运行时间：2026-08-11 20:37:31 UTC
- 运行状态：成功
- 本次总论文数：15
- 精读区：6
- 速读区：9

### 今日简报（AI）
今日共推荐15篇论文，精读2篇、速读3篇，核心聚焦KV Cache压缩与长上下文效率优化。  
最值得关注两篇满分精读：CommitKV通过生命周期感知的提交转换优化多轮智能体缓存，SPECTRA用谱变换编码突破2-bit压缩极限，均达9.0分。  
建议后续优先追踪KV Cache稀疏预取（如OasisKV）与跨模态长文本压缩（VLZip），兼顾检索增强的AnchorFold。
- 详情：[/202608/11/README](/202608/11/README)

### 精读区论文标签
1. [CommitKV: Lifecycle-Aware KV Cache Compression via Commit Transitions for Multi-Turn Agents](/202608/11/2608.07855v1-commitkv-lifecycle-aware-kv-cache-compression-via-commit-transitions-for-multi-turn-agents)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向多轮智能体的生命周期感知KV缓存压缩
2. [SPECTRA: Pushing the KV Cache Beyond the 2-Bit Cliff via Spectral Transform Coding](/202608/11/2608.07915v1-spectra-pushing-the-kv-cache-beyond-the-2-bit-cliff-via-spectral-transform-coding)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于谱变换编码对KV缓存进行压缩，突破2比特量化极限
3. [RotaryQuant: Fitting 120B MoE Models on Consumer Hardware via Fused Compressed-Space Attention](/202608/11/2608.08081v1-rotaryquant-fitting-120b-moe-models-on-consumer-hardware-via-fused-compressed-space-attention)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向大规模MoE模型的KV缓存压缩与融合压缩空间注意力量化
4. [VoxZip: Semantic-Anchored Temporal KV Cache Compression for Long-Context Audio Inference](/202608/11/2608.08569v1-voxzip-semantic-anchored-temporal-kv-cache-compression-for-long-context-audio-inference)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：以ASR转录为语义锚点的无训练KV缓存压缩，提升语音大模型长上下文推理效率
5. [RippleKV: Cross-Layer KV Cache Allocation via Perturbation Propagation](/202608/11/2608.08684v1-ripplekv-cross-layer-kv-cache-allocation-via-perturbation-propagation)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于扰动传播的跨层KV缓存预算分配，用于长上下文LLM推理
6. [DistillCache: KL-Guided Adaptive KV-Cache Eviction for Memory-Efficient LLM Inference](/202608/11/2608.08878v1-distillcache-kl-guided-adaptive-kv-cache-eviction-for-memory-efficient-llm-inference)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：用强化学习进行自适应KV缓存驱逐

### 速读区论文标签
1. [OasisKV: Scaling In-Decode KV Cache Beyond HBM with Lookahead Sparse Prefetching](/202608/11/2608.08097v1-oasiskv-scaling-in-decode-kv-cache-beyond-hbm-with-lookahead-sparse-prefetching)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：通过前视稀疏预取将解码阶段KV缓存扩展到HBM之外
2. [VLZip: Unified Visual and Textual Compression for Interleaved Long-Context Modeling](/202608/11/2608.08630v1-vlzip-unified-visual-and-textual-compression-for-interleaved-long-context-modeling)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：面向交错长上下文的多模态统一压缩，提升VLM推理效率
3. [AnchorFold: A Focus-Then-Fold Framework via Recursive Attention Propagation for Efficient Multi-Vector Visual Document Retrieval](/202608/11/2608.08732v1-anchorfold-a-focus-then-fold-framework-via-recursive-attention-propagation-for-efficient-multi-vector-visual-document-retrieval)  
   标签：评分：8.0/10、query:multimodal
   evidence：基于注意力传播的索引压缩实现高效多向量视觉文档检索，直接面向多模态检索
4. [Omni2LoRA: Coherence-Preserving Parametric Memory for Efficient Omni Language Models](/202608/11/2608.09227v1-omni2lora-coherence-preserving-parametric-memory-for-efficient-omni-language-models)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：通过LoRA参数化记忆压缩降低全模态语言模型长序列推理的内存瓶颈
5. [Linearized 2-Simplicial Attention](/202608/11/2608.09307v1-linearized-2-simplicial-attention)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：线性化注意力机制，固定大小状态实现线性复杂度
6. [MixFormer: Linear Transformer with Mixture of Memory Experts](/202608/11/2608.09468v1-mixformer-linear-transformer-with-mixture-of-memory-experts)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：带混合记忆专家的线性Transformer，面向高效长上下文建模
7. [HSMLA: Hierarchical Softmax Multi-scale Linear Attention for Efficient Vision Transformers](/202608/11/2608.07616v1-hsmla-hierarchical-softmax-multi-scale-linear-attention-for-efficient-vision-transformers)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：面向高效视觉Transformer的多尺度线性注意力机制
8. [Sparse Attention to Emotion: Efficient Facial Emotion Recognition via Token Reduction](/202608/11/2608.08873v1-sparse-attention-to-emotion-efficient-facial-emotion-recognition-via-token-reduction)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：通过令牌缩减的稀疏注意力实现高效视觉Transformer
9. [Decoupling semantics from vision: A framework for faithful visual-text compression evaluation](/202608/11/2608.01848v1-decoupling-semantics-from-vision-a-framework-for-faithful-visual-text-compression-evaluation)  
   标签：评分：6.0/10、query:multimodal
   evidence：面向多模态大模型的视觉-文本压缩评估框架


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
