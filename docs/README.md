<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-05
- 运行时间：2026-08-05 21:21:21 UTC
- 运行状态：成功
- 本次总论文数：18
- 精读区：8
- 速读区：10

### 今日简报（AI）
今日完成18篇论文阅读，精读8篇、速读10篇，重点聚焦KV Cache压缩与长序列稀疏注意力优化。最值得关注的是《AnchorKV》（10分）提出锚点残差式KV缓存压缩，以及《LongCat Sparse Attention》（9分）用跨层索引实现流式稀疏注意力，二者均直击大模型推理效率瓶颈。建议优先精读上述两篇，并顺带浏览《Opt.Gear Technical Report》（8分）了解工程优化实践。
- 详情：[/202608/05/README](/202608/05/README)

### 精读区论文标签
1. [AnchorKV: Anchor-Residual KV Cache Compression](/202608/05/2608.02901v1-anchorkv-anchor-residual-kv-cache-compression)  
   标签：评分：10.0/10、query:sparse-attn
   evidence：使用锚点残差实现20倍压缩且不丢弃token的KV缓存压缩
2. [LongCat Sparse Attention: Taming the Lightning via Streaming-aware Hierarchical Cross-Layer Indexing](/202608/05/2608.01662v2-longcat-sparse-attention-taming-the-lightning-via-streaming-aware-hierarchical-cross-layer-indexing)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向长上下文Transformer的稀疏注意力机制与硬件高效索引
3. [Output-Aware Rotation for INT2 KV-Cache Quantization](/202608/05/2608.02691v1-output-aware-rotation-for-int2-kv-cache-quantization)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于输出感知旋转的INT2 KV缓存量化方法
4. [Maglev: Sliding Recurrent Memory](/202608/05/2608.02870v1-maglev-sliding-recurrent-memory)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：带滑窗注意力与固定大小记忆的循环Transformer
5. [ATFlash: Per-RoPE-Wavelength Attention Windows for Compute/Memory-Efficient LLM Inference](/202608/05/2608.02947v1-atflash-per-rope-wavelength-attention-windows-for-computememory-efficient-llm-inference)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：提出基于RoPE波长的注意力窗口剪枝，实现计算和内存高效的长上下文推理
6. [SAKI: Score-Aware Low-Rank Key Indexing for Long-Context KV Retrieval](/202608/05/2608.03228v1-saki-score-aware-low-rank-key-indexing-for-long-context-kv-retrieval)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：保持注意力分数的低秩KV缓存压缩，用于长上下文检索
7. [TaskPress: Query-Agnostic KV Cache Compression via Task-Guided Pruning](/202608/05/2608.03276v1-taskpress-query-agnostic-kv-cache-compression-via-task-guided-pruning)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：基于任务引导剪枝的KV缓存压缩，查询无关
8. [SPADE: An Input-Adaptive Sparse Attention Engine for Fast Video Diffusion Models Inference](/202608/05/2608.03335v1-spade-an-input-adaptive-sparse-attention-engine-for-fast-video-diffusion-models-inference)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向视频扩散Transformer的免训练输入自适应稀疏注意力引擎

### 速读区论文标签
1. [Opt.Gear Technical Report](/202608/05/2608.01034v2-optgear-technical-report)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：通过卷积KV门控混合器与局部-全局注意力降低端侧LLM的KV缓存内存
2. [UEmbed: Unified Sparse and Dense Multimodal Embeddings](/202608/05/2608.02583v1-uembed-unified-sparse-and-dense-multimodal-embeddings)  
   标签：评分：8.0/10、query:multimodal
   evidence：面向检索的统一稀疏/稠密多模态嵌入模型
3. [Unified Lookup-Table Inference with Signed-Digit K/V Caches for Ternary LLMs](/202608/05/2608.03229v1-unified-lookup-table-inference-with-signed-digit-kv-caches-for-ternary-llms)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：用有符号数字K/V缓存表示实现三值大模型注意力缓存压缩
4. [Heterogeneous LLM Serving with General-Purpose Processing-Near-Memory for Retrieval-Based Sparse Attention](/202608/05/2608.03555v1-heterogeneous-llm-serving-with-general-purpose-processing-near-memory-for-retrieval-based-sparse-attention)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：面向检索式稀疏注意力的异构PNM-GPU服务系统并迁移KV缓存
5. [SMM Transformer: Leveraging Spiking Neural Networks for Multimodal Tasks](/202608/05/2608.01622v1-smm-transformer-leveraging-spiking-neural-networks-for-multimodal-tasks)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：脉冲Transformer以事件驱动稀疏计算替代密集softmax注意力
6. [CRAFT: Compression via Recursive Adaptive Fusion of Video Tokens for Vision-Language Models](/202608/05/2608.01644v1-craft-compression-via-recursive-adaptive-fusion-of-video-tokens-for-vision-language-models)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：通过视频token压缩降低视觉语言模型预填充阶段的内存与计算开销
7. [Mamba with Hierarchical Memory: Solving Representation Bottleneck in Long Sequence Modeling](/202608/05/2608.02347v1-mamba-with-hierarchical-memory-solving-representation-bottleneck-in-long-sequence-modeling)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：面向Mamba长序列建模的层级记忆压缩
8. [PI-Mem: Pushing Long-Context Reasoning to 3.6M Tokens with Parallel-Iterative Memory](/202608/05/2608.03048v1-pi-mem-pushing-long-context-reasoning-to-36m-tokens-with-parallel-iterative-memory)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：面向长上下文推理的并行迭代记忆压缩，类似KV缓存管理
9. [Structured Memory for Edge Language Models: Persistent Context and Corpus Retrieval via O(1) SSM State Injection](/202608/05/2608.02560v1-structured-memory-for-edge-language-models-persistent-context-and-corpus-retrieval-via-o1-ssm-state-injection)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：通过SSM状态注入将检索预填充降为O(1)，并规避Transformer KV缓存增长，实现边缘端内存压缩
10. [When Should Graph Attention Be Sparse? Learning a Per-Edge Tsallis Index](/202608/05/2608.02938v1-when-should-graph-attention-be-sparse-learning-a-per-edge-tsallis-index)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：利用Tsallis熵在图中学习稀疏注意力形状


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
