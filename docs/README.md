<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-13
- 运行时间：2026-07-13 21:31:16 UTC
- 运行状态：成功
- 本次总论文数：11
- 精读区：6
- 速读区：5

### 今日简报（AI）
今日聚焦多模态LLM推理置信度与语音LLM缓存压缩，精读两篇9分论文。最值得关注的方向是：无需微调即可评估MLLM定位能力的“Propose and Attend”，以及针对语音模型的高效KV缓存压缩方法。建议深入阅读这两篇精读文章，并尝试将量化与缓存调度技术（如Qwen3.5-4B的量化与MOSAIC层间组合）应用于实际推理优化。
- 详情：[/202607/13/README](/202607/13/README)

### 精读区论文标签
1. [Propose and Attend: Training-free MLLM Grounding Confidence via Multi-Token Localized Attention](/202607/13/2607.05978v1-propose-and-attend-training-free-mllm-grounding-confidence-via-multi-token-localized-attention)  
   标签：评分：9.0/10、query:multimodal
   evidence：无训练的多模态大模型定位置信度，用于幻觉检测
2. [Compress the Cache, Not the Speech Embedding: KV Compression for Efficient Speech LLMs](/202607/13/2607.06827v1-compress-the-cache-not-the-speech-embedding-kv-compression-for-efficient-speech-llms)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：语音大语言模型KV缓存压缩
3. [COBS: Cumulant Order Block Sparse Attention](/202607/13/2607.09052v1-cobs-cumulant-order-block-sparse-attention)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：块稀疏注意力缓解KV缓存读取瓶颈
4. [A Survey on the Green Development of Large Models: From Resource-Efficient Architectures to Hardware-Software Co-Design](/202607/13/2607.09084v1-a-survey-on-the-green-development-of-large-models-from-resource-efficient-architectures-to-hardware-software-co-design)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：综述涵盖注意力算子优化、模型稀疏化及高效架构
5. [STEEL: Sparsity-Aware Fused Attention for Energy-Efficient Long-Sequence Inference on AMD's XDNA NPU](/202607/13/2607.09385v1-steel-sparsity-aware-fused-attention-for-energy-efficient-long-sequence-inference-on-amds-xdna-npu)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：面向NPU的稀疏感知融合注意力
6. [Do All Visual Tokens Matter Equally? Object-Evidence Preserving Token Merging for Vision-Language Retrieval](/202607/13/2607.04605v1-do-all-visual-tokens-matter-equally-object-evidence-preserving-token-merging-for-vision-language-retrieval)  
   标签：评分：8.0/10、query:multimodal
   evidence：对象感知的令牌合并用于视觉语言检索

### 速读区论文标签
1. [Quantize the Target, Quantize the Drafter: Efficient Inference with Qwen3.5-4B](/202607/13/2607.04244v2-quantize-the-target-quantize-the-drafter-efficient-inference-with-qwen35-4b)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：使用滑动窗口注意力，一种稀疏注意力模式
2. [MOSAIC: Adaptive Inter-layer Composition for Efficient Heterogeneous Vision-Language Models](/202607/13/2607.09029v1-mosaic-adaptive-inter-layer-composition-for-efficient-heterogeneous-vision-language-models)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：集成稀疏和线性注意力机制以构建高效视觉-语言模型
3. [General Non-Clairvoyant KV-Cache Scheduling via Regime-Aware Routing](/202607/13/2607.09248v1-general-non-clairvoyant-kv-cache-scheduling-via-regime-aware-routing)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：面向LLM推理的非预知KV缓存调度算法
4. [Foveation-Guided Dynamic Token Selection for Robust and Efficient Vision Transformers](/202607/13/2607.09480v1-foveation-guided-dynamic-token-selection-for-robust-and-efficient-vision-transformers)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：注视引导的动态令牌选择，实现高效视觉Transformer
5. [Quantize the Target, Quantize the Drafter: Efficient Inference with Qwen3.5-4B](/202607/13/2607.04244v1-quantize-the-target-quantize-the-drafter-efficient-inference-with-qwen35-4b)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：结合量化和滑动窗口注意力的高效推理


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
