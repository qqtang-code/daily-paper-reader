<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-18
- 运行时间：2026-06-18 22:38:01 UTC
- 运行状态：成功
- 本次总论文数：19
- 精读区：7
- 速读区：12

### 今日简报（AI）
今日共分析19篇论文，精读7篇、速读12篇，重点关注QK归一化注意力机制优化和视觉链式推理两大突破。  
最值得关注的是《QK-Normed MLA》通过避免完整键缓存提升效率，以及《Gen-VCoT》用扩散模型生成视觉中间表示的推理方法。  
下一步可聚焦多模态大模型幻觉检测（如ClinHallu基准）与长文本混合架构（GSS-Transformer）的实际应用效果。
- 详情：[/202606/18/README](/202606/18/README)

### 精读区论文标签
1. [QK-Normed MLA: QK normalization without full key caching](/202606/18/2606.16310v1-qk-normed-mla-qk-normalization-without-full-key-caching)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：在不完整键缓存情况下实现QK归一化，提升MLA解码效率
2. [Gen-VCoT: Generative Visual Chain-of-Thought Reasoning via Diffusion-Based RGB Intermediate Representations](/202606/18/2606.16783v1-gen-vcot-generative-visual-chain-of-thought-reasoning-via-diffusion-based-rgb-intermediate-representations)  
   标签：评分：9.0/10、query:mm-cot
   evidence：基于扩散的视觉链式推理中间表示
3. [KVEraser: Learning to Steer KV Cache for Efficient Localized Context Erasing](/202606/18/2606.17034v1-kveraser-learning-to-steer-kv-cache-for-efficient-localized-context-erasing)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：学习的KV缓存编辑方法用于高效局部上下文擦除
4. [Context-Aware RL for Agentic and Multimodal LLMs](/202606/18/2606.17053v1-context-aware-rl-for-agentic-and-multimodal-llms)  
   标签：评分：9.0/10、query:mm-cot
   evidence：上下文感知强化学习提升长程推理和多模态性能
5. [Visuals Lie, Consistency Speaks: Disentangling Spatial Attention from Reliability in Vision-Language Models](/202606/18/2606.17389v1-visuals-lie-consistency-speaks-disentangling-spatial-attention-from-reliability-in-vision-language-models)  
   标签：评分：9.0/10、query:multimodal
   evidence：视觉语言模型中的幻觉检测
6. [Dual Dimensionality for Local and Global Attention](/202606/18/2606.18587v1-dual-dimensionality-for-local-and-global-attention)  
   标签：评分：9.0/10、query:sparse-attn
   evidence：通过距离自适应表示压缩KV缓存
7. [DLWM: Diverse Latent World Models for Efficient Multimodal Reasoning](/202606/18/2606.15160v1-dlwm-diverse-latent-world-models-for-efficient-multimodal-reasoning)  
   标签：评分：8.0/10、query:mm-cot
   evidence：提出多样化潜在世界模型用于多模态推理，解决长链推理

### 速读区论文标签
1. [ClinHallu: A Benchmark for Diagnosing Stage-Wise Hallucinations in Medical MLLM Reasoning](/202606/18/2606.14697v1-clinhallu-a-benchmark-for-diagnosing-stage-wise-hallucinations-in-medical-mllm-reasoning)  
   标签：评分：8.0/10、query:multimodal
   evidence：用于诊断医学多模态大模型推理中分阶段幻觉的基准，直接关注幻觉原因
2. [Long-Context Modeling via GSS-Transformer Hybrid Architecture with Learnable Mixing](/202606/18/2606.16093v1-long-context-modeling-via-gss-transformer-hybrid-architecture-with-learnable-mixing)  
   标签：评分：8.0/10、query:sparse-attn
   evidence：通过GQA和混合架构实现高效注意力
3. [Cascaded Sparse Autoencoders Learn Multi-Level Visual Concepts in Multimodal LLMs](/202606/18/2606.16193v1-cascaded-sparse-autoencoders-learn-multi-level-visual-concepts-in-multimodal-llms)  
   标签：评分：8.0/10、query:multimodal
   evidence：多模态大语言模型中层次化视觉概念学习
4. [UniDDT: Unifying Multimodal Understanding and Generation with Decoupled Diffusion Transformer](/202606/18/2606.16255v1-uniddt-unifying-multimodal-understanding-and-generation-with-decoupled-diffusion-transformer)  
   标签：评分：8.0/10、query:multimodal
   evidence：解耦扩散Transformer统一多模态理解与生成
5. [GRIP: Feedback-Guided Prompt Retrieval for Large Multimodal Models](/202606/18/2606.12744v1-grip-feedback-guided-prompt-retrieval-for-large-multimodal-models)  
   标签：评分：7.0/10、query:multimodal
   evidence：反馈引导的多模态上下文学习示例检索
6. [Text-Driven Fusion for Infrared and Visible Images: Achieving Image Scene Adaptation on Hyperbolic Space](/202606/18/2606.15104v1-text-driven-fusion-for-infrared-and-visible-images-achieving-image-scene-adaptation-on-hyperbolic-space)  
   标签：评分：7.0/10、query:multimodal
   evidence：使用文本驱动的双曲空间学习融合红外与可见光图像的多模态方法
7. [MoECa: Aligning Feature Reuse with Expert Decomposition in Diffusion Transformers](/202606/18/2606.15615v1-moeca-aligning-feature-reuse-with-expert-decomposition-in-diffusion-transformers)  
   标签：评分：7.0/10、query:sparse-attn
   evidence：面向扩散Transformer的细粒度缓存，结合混合专家稀疏激活
8. [The Truth Stays in the Family: Enhancing Contextual Grounding via Inherited Truthful Heads in Model Lineages](/202606/18/2606.15821v1-the-truth-stays-in-the-family-enhancing-contextual-grounding-via-inherited-truthful-heads-in-model-lineages)  
   标签：评分：7.0/10、query:multimodal
   evidence：多模态LLM中上下文真实性的继承用于减少幻觉
9. [G-Long: Graph-Enhanced Memory Management for Efficient Long-Term Dialogue Agents](/202606/18/2606.13115v1-g-long-graph-enhanced-memory-management-for-efficient-long-term-dialogue-agents)  
   标签：评分：6.0/10、query:sparse-attn
   evidence：在长对话中使用注意力感知重要性评分进行记忆管理，涉及长上下文注意力
10. [Context-aware Modality-Topology Co-Alignment for Multimodal Attributed Graphs](/202606/18/2606.14172v1-context-aware-modality-topology-co-alignment-for-multimodal-attributed-graphs)  
   标签：评分：6.0/10、query:multimodal
   evidence：多模态属性图表示学习用于理解
11. [Conditional Multi-Event Temporal Grounding in Long-Form Video](/202606/18/2606.15320v1-conditional-multi-event-temporal-grounding-in-long-form-video)  
   标签：评分：6.0/10、query:multimodal
   evidence：长视频中条件多事件时间定位使用多模态大模型
12. [From Frames to Temporal Graphs: In-Context Egocentric Action Recognition with Vision-Language Models](/202606/18/2606.15417v1-from-frames-to-temporal-graphs-in-context-egocentric-action-recognition-with-vision-language-models)  
   标签：评分：6.0/10、query:multimodal
   evidence：使用时序图的视觉语言模型进行自我中心动作推理


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
