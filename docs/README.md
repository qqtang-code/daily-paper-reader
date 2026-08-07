<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-07
- 运行时间：2026-08-07 02:08:42 UTC
- 运行状态：成功
- 本次总论文数：9
- 精读区：5
- 速读区：4

### 今日简报（AI）
今日精读5篇、速读4篇，焦点集中在注意力机制与KV cache量化优化。最值得关注的是《Training-Free Hashing-Based Attention》与《Spend Bits Where Queries Look》，分别提出免训练哈希注意力和保注意力变换下的向量量化方法。建议优先精读这两篇高分论文，以掌握当前长序列推理加速的核心思路。
- 详情：[/202608/07/README](/202608/07/README)

### 精读区论文标签
1. [Training-Free Hashing-Based Attention via Binary Principal Components](/202608/07/2608.04405v1-training-free-hashing-based-attention-via-binary-principal-components)  
   标签：评分：10.0/10、query:sparse-attn
   evidence：面向长上下文LLM的免训练哈希稀疏注意力
2. [Spend Bits Where Queries Look: KV Cache Vector Quantization with Attention-Preserving Transforms](/202608/07/2608.04074v1-spend-bits-where-queries-look-kv-cache-vector-quantization-with-attention-preserving-transforms)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：提出带有注意力保持变换的KV缓存向量量化，面向带宽受限的长上下文LLM解码。
3. [Fewer Tokens, Smaller Cache: Reward-Coordinated Efficient Reasoning](/202608/07/2608.04771v1-fewer-tokens-smaller-cache-reward-coordinated-efficient-reasoning)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：针对大型推理模型链式思考过程的KV缓存压缩
4. [Maglev: Sliding Recurrent Memory](/202608/07/2608.02870v2-maglev-sliding-recurrent-memory)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：固定大小记忆的递归Transformer，泛化滑窗注意力
5. [Heterogeneous LLM Serving with General-Purpose Processing-Near-Memory for Retrieval-Based Sparse Attention](/202608/07/2608.03555v1-heterogeneous-llm-serving-with-general-purpose-processing-near-memory-for-retrieval-based-sparse-attention)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：面向检索式稀疏注意力的KV缓存外置与近数据计算设计，支持百万token上下文

### 速读区论文标签
1. [Bole: Efficient Tree Speculation for Hybrid-Attention Language Models](/202608/07/2608.01651v1-bole-efficient-tree-speculation-for-hybrid-attention-language-models)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：通过树推测实现混合注意力LLM的高效解码
2. [Mamba with Hierarchical Memory: Solving Representation Bottleneck in Long Sequence Modeling](/202608/07/2608.02347v2-mamba-with-hierarchical-memory-solving-representation-bottleneck-in-long-sequence-modeling)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：提出层次记忆Mamba，通过工作记忆与长期记忆缓解循环线性注意力模型的表示瓶颈
3. [UEmbed: Unified Sparse and Dense Multimodal Embeddings](/202608/07/2608.02583v1-uembed-unified-sparse-and-dense-multimodal-embeddings)  
   标签：评分：7.0/10、query:multimodal
   evidence：仅解码器多模态嵌入，同时生成稀疏词汇与稠密表示用于检索
4. [Decoupling semantics from vision: A framework for faithful visual-text compression evaluation](/202608/07/2608.01848v1-decoupling-semantics-from-vision-a-framework-for-faithful-visual-text-compression-evaluation)  
   标签：评分：6.0/10、query:multimodal
   evidence：面向多模态大模型的视觉-文本压缩质量评估框架，解决MLLM先验与评测基准问题


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
