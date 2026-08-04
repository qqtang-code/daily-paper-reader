<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-04
- 运行时间：2026-08-04 21:33:45 UTC
- 运行状态：成功
- 本次总论文数：18
- 精读区：7
- 速读区：11

### 今日简报（AI）
1) 今日18篇推荐，精读7篇，重点聚焦长上下文问答与KV缓存压缩。  
2) 最值得看：SeDeM与S4R两篇高分工作，均以选择性采样/子空间重构压缩隐藏状态记忆，显著缓解长上下文显存压力。  
3) 普通读者建议优先精读这两篇，并留意Opt.Gear与多时间尺度视觉-语言桥接的速读关联。
- 详情：[/202608/04/README](/202608/04/README)

### 精读区论文标签
1. [SeDeM: Selective Decompression of Hidden-State Memories for Long-Context Question Answering](/202608/04/2608.00311v1-sedem-selective-decompression-of-hidden-state-memories-for-long-context-question-answering)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：直接针对KV缓存增长，通过上下文压缩与选择性解压缩降低存储
2. [S$^4$R: Selective Sampling, Subspaces, and Sparse Reconstruction for Compressed Long-Context KV Caching](/202608/04/2608.00528v1-s4r-selective-sampling-subspaces-and-sparse-reconstruction-for-compressed-long-context-kv-caching)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：利用低秩子空间与稀疏重建压缩长上下文KV缓存，直接针对KV缓存压缩
3. [Practical Online KV Cache Compaction for LLM Agents: An Empirical Study](/202608/04/2608.00902v1-practical-online-kv-cache-compaction-for-llm-agents-an-empirical-study)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向LLM智能体的在线KV缓存压缩，涵盖token驱逐与注意力匹配策略
4. [RestoreKV: Recovering Full-Cache Behavior Under Aggressive Query-Agnostic KV Cache Eviction](/202608/04/2608.01247v1-restorekv-recovering-full-cache-behavior-under-aggressive-query-agnostic-kv-cache-eviction)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：在固定KV缓存预算下用学习式恢复补偿驱逐损失
5. [LongCat Sparse Attention: Taming the Lightning via Streaming-aware Hierarchical Cross-Layer Indexing](/202608/04/2608.01662v1-longcat-sparse-attention-taming-the-lightning-via-streaming-aware-hierarchical-cross-layer-indexing)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向稀疏注意力的软硬件协同设计，采用流感知和跨层索引优化
6. [DART: Decoded Attention over Recurrent States for Efficient Long-Context Sequence Modeling](/202608/04/2608.02032v1-dart-decoded-attention-over-recurrent-states-for-efficient-long-context-sequence-modeling)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：从Mamba-2的SSD视角将SSM状态视为压缩KV缓存，并引入解码注意力
7. [Token Radius Attention for Efficient Video Generation](/202608/04/2608.02504v1-token-radius-attention-for-efficient-video-generation)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：无训练稀疏注意力，按查询熵映射到令牌特化半径以提升视频生成效率

### 速读区论文标签
1. [Opt.Gear Technical Report](/202608/04/2608.01034v1-optgear-technical-report)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：结合卷积KV门控混合器与局部-全局注意力来压缩KV缓存内存
2. [Perspectives on Tsallis Statistics for Artificial Intelligence](/202608/04/2608.01223v1-perspectives-on-tsallis-statistics-for-artificial-intelligence)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：涵盖稀疏注意力机制（sparsemax、α-entmax）
3. [Linear Multi-Timescale Retention as a Memory-Efficient Vision-Language Bridge](/202608/04/2608.01614v1-linear-multi-timescale-retention-as-a-memory-efficient-vision-language-bridge)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：用线性保留机制替代softmax注意力，降低显存开销，属于高效注意力机制
4. [Understanding Sparse Attention Selectivity in Long-Context Foundation Models via Counterfactual Evaluation](/202608/04/2608.01676v1-understanding-sparse-attention-selectivity-in-long-context-foundation-models-via-counterfactual-evaluation)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：对长上下文模型中的块稀疏注意力进行反事实审计
5. [Spatial Prefix Caching for Wireless Edge LLM Inference: A Stochastic-Geometry and Queueing Framework](/202608/04/2608.01126v1-spatial-prefix-caching-for-wireless-edge-llm-inference-a-stochastic-geometry-and-queueing-framework)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：面向LLM推理的前缀KV缓存与TTFT优化
6. [Think in Sets for Streaming Video Token Compression](/202608/04/2608.01169v1-think-in-sets-for-streaming-video-token-compression)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：将流式视频令牌压缩建模为带历史参考的集合选择
7. [Same Semantics, Different Paths: Self-Improving Alignment for Vision-Text Compression](/202608/04/2608.02109v1-same-semantics-different-paths-self-improving-alignment-for-vision-text-compression)  
   标签：评分：7.0/10、query:multimodal
   evidence：面向视觉-文本压缩的自监督对齐，保留多模态模型中的语言语义
8. [Messages, Not Tokens: Grounded Coresets for Faithful VLM Compression](/202608/04/2608.02134v1-messages-not-tokens-grounded-coresets-for-faithful-vlm-compression)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：压缩持久化于提示KV缓存中的视觉token，降低推理开销
9. [OmniCache: Multidimensional Hierarchical Feature Caching For Diffusion Models](/202608/04/2607.23844v1-omnicache-multidimensional-hierarchical-feature-caching-for-diffusion-models)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：面向注意力密集型扩散模型的层次化特征缓存
10. [Interpretability-Guided Soft Pruning of Attention Heads in Vision Transformers](/202608/04/2608.00264v1-interpretability-guided-soft-pruning-of-attention-heads-in-vision-transformers)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：通过可解释性分析对视觉Transformer注意力头进行软剪枝，降低计算与内存开销
11. [DeltaFlow: Noise-Adaptive Bidirectional Gated Delta Networks for Embedded Language Flows](/202608/04/2608.01240v1-deltaflow-noise-adaptive-bidirectional-gated-delta-networks-for-embedded-language-flows)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：用高效循环门控Delta网络替代嵌入式语言流中的二次注意力


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
