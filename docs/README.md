<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-17
- 运行时间：2026-08-17 20:35:25 UTC
- 运行状态：成功
- 本次总论文数：6
- 精读区：2
- 速读区：4

### 今日简报（AI）
今日聚焦KV缓存压缩与线性注意力遗忘机制，共精读2篇、速读4篇。  
最值得关注：Transform Coding视角的KV压缩（10分）与线性注意力“第二擦除方向”（9分），直击长序列推理效率。  
建议优先精读这两篇论文，核心思路可迁移至显存优化与长上下文模型部署。
- 详情：[/202608/17/README](/202608/17/README)

### 精读区论文标签
1. [KV Cache Compression Through the Lens of Transform Coding](/202608/17/2608.14191v1-kv-cache-compression-through-the-lens-of-transform-coding)  
   标签：评分：10.0/10、query:sparse-attn
   evidence：通过变换编码和率失真理论进行注意力感知的KV缓存压缩
2. [The Query Knows What to Forget: A Second Erase Direction for Linear Attention](/202608/17/2608.13668v1-the-query-knows-what-to-forget-a-second-erase-direction-for-linear-attention)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：提出查询导出的擦除方向以改进线性注意力，减少长上下文干扰

### 速读区论文标签
1. [Lapis: Laplacian Spiking Attention via First-Spike Timing and Membrane Leakage](/202608/17/2608.11865v1-lapis-laplacian-spiking-attention-via-first-spike-timing-and-membrane-leakage)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：利用首脉冲延迟和拉普拉斯核提出新型脉冲注意力，适用于高效Transformer
2. [Self-Correcting Long-Horizon Search Agents via Tree-Structured Memory](/202608/17/2608.10676v1-self-correcting-long-horizon-search-agents-via-tree-structured-memory)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：用树结构化记忆压缩LLM搜索轨迹并保留证据，解决上下文增长问题
3. [Consolidator: Learning Persistent Routed Memory Across Context Boundaries](/202608/17/2608.11701v1-consolidator-learning-persistent-routed-memory-across-context-boundaries)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：跨上下文边界的持久记忆；清除KV缓存并利用长期记忆进行长上下文处理
4. [Reduced Matrix Multiplication: Input-Adaptive Matrix-Product Reduction for LLM Inference](/202608/17/2608.13426v1-reduced-matrix-multiplication-input-adaptive-matrix-product-reduction-for-llm-inference)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：无训练、输入自适应的Transformer矩阵乘法约简，可提升LLM推理效率


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
