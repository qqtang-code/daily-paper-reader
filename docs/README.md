<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-31
- 运行时间：2026-07-31 21:40:51 UTC
- 运行状态：成功
- 本次总论文数：12
- 精读区：6
- 速读区：6

### 今日简报（AI）
今日12篇论文聚焦大模型推理优化，精读主打KV缓存与推测解码改造。最值得看：MLA草稿模型的“功能重建”替代KV重建，以及“反因果意外”驱动的缓存管理策略。建议优先关注这两项KV缓存方向，并延伸浏览多模态剪枝/压缩方法（SepPrune、ReToken、OmniScope）。
- 详情：[/202607/31/README](/202607/31/README)

### 精读区论文标签
1. [Beyond KV Reconstruction: Functional Reconstruction for MLA Draft Models in Speculative Decoding](/202607/31/2607.27269v1-beyond-kv-reconstruction-functional-reconstruction-for-mla-draft-models-in-speculative-decoding)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：MLA潜在状态压缩KV缓存；面向草稿模型的功能重建
2. [Back from the Future: Key-Value Cache Management by Counter-Causal Surprise](/202607/31/2607.27600v1-back-from-the-future-key-value-cache-management-by-counter-causal-surprise)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：通过反因果惊喜进行键值缓存压缩与驱逐
3. [Recall Before You Rank: Similarity-Guided Top-$K$ Reuse for Efficient Long-Context Attention](/202607/31/2607.27692v1-recall-before-you-rank-similarity-guided-top-k-reuse-for-efficient-long-context-attention)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：通过复用历史检索决策加速基于KV缓存的Top-K稀疏注意力
4. [A Sparse Glimpse of the Whole: Train-Free Self-Speculative Decoding](/202607/31/2607.27735v1-a-sparse-glimpse-of-the-whole-train-free-self-speculative-decoding)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：提出免训练自推测解码框架SparseSpec-L，利用动态稀疏化且可回收的KV缓存加速长上下文推理。
5. [SemPIC: Learning Semantic Position-Independent KV Caches](/202607/31/2607.28069v1-sempic-learning-semantic-position-independent-kv-caches)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：学习语义位置无关的 KV 缓存，使文档在上下文变化时仍可复用
6. [Structured Redundancy Modeling for Efficient Visual Token Pruning in High-Resolution MLLMs](/202607/31/2607.23046v1-structured-redundancy-modeling-for-efficient-visual-token-pruning-in-high-resolution-mllms)  
   标签：评分：8.0/10、query:multimodal
   evidence：针对高分辨率MLLMs的视觉Token爆炸问题，提出单前向剪枝器SFPruner进行冗余控制。

### 速读区论文标签
1. [SepPrune:A Separator-based Pruning Framework for Efficient Multimodal Large Language Models](/202607/31/2607.25818v1-sepprunea-separator-based-pruning-framework-for-efficient-multimodal-large-language-models)  
   标签：评分：8.0/10、query:multimodal
   evidence：提出SepPrune，利用分隔符Token作为统一查询对视觉Token进行排序选择，实现高效剪枝。
2. [ReToken: One Token to Improve Vision-Language Models for Visual Retrieval](/202607/31/2607.28627v1-retoken-one-token-to-improve-vision-language-models-for-visual-retrieval)  
   标签：评分：8.0/10、query:multimodal
   evidence：从视觉KV缓存中稀疏选择相关视觉令牌以改进视觉语言模型的检索
3. [OmniScope: Modality-Decoupled Token Compression for Omnimodal Large Language Models](/202607/31/2607.23193v2-omniscope-modality-decoupled-token-compression-for-omnimodal-large-language-models)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：全模态大模型中的模态解耦token压缩，降低内存开销
4. [Understanding Is Done Early: A Depth Division of Labor in Large Language Models and Its Use for Unbounded-Context Memory](/202607/31/2607.28263v1-understanding-is-done-early-a-depth-division-of-labor-in-large-language-models-and-its-use-for-unbounded-context-memory)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：缓存中间层残差状态并重计算上层，使长上下文内存与计算不再随存储长度增长
5. [OmniScope: Modality-Decoupled Token Compression for Omnimodal Large Language Models](/202607/31/2607.23193v1-omniscope-modality-decoupled-token-compression-for-omnimodal-large-language-models)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：面向全模态大模型的免训练token压缩，按模态独立估计相关性并修剪视觉token
6. [Disentangling Semantic Attention from Structural Bias in the Attention Manifold](/202607/31/2607.24017v1-disentangling-semantic-attention-from-structural-bias-in-the-attention-manifold)  
   标签：评分：6.0/10、query:multimodal
   evidence：研究多模态大模型中视觉注意力汇/结构偏差，与视觉token注意力分配相关


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
