# 日报 · 2026-09-10

- 最近生成时间：2026-09-10 22:17:28 UTC
- 今日累计更新：1 次
- 今日累计推荐总数：27
- 精读区：16
- 速读区：11

## 今日简报（AI）
今日精读16篇、速读11篇共27篇论文，重点关注长上下文大模型的注意力与KV缓存优化。最值得看的是CRISP（9.0）的输入自适应稀疏预填充与HeadWiseKV（9.0）的分头缓存驻留，速读中语言模型自主控制注意力（8.0）也值得跟进。普通读者可先读这两篇精读，建立“按输入和头维度省算力”的思路。

## 精读区
1. [CRISP: Cliff-awaRe Input-adaptive Sparse Prefilling with Structural-Mass-Motivated Routing](/202609/10/2609.01925v1-crisp-cliff-aware-input-adaptive-sparse-prefilling-with-structural-mass-motivated-routing) （9.0/10）
2. [HeadWiseKV: Budgeted Per-Head Cache Residency for Hybrid Long-Context Language Models](/202609/10/2609.02029v1-headwisekv-budgeted-per-head-cache-residency-for-hybrid-long-context-language-models) （9.0/10）
3. [SGD-KV: Summarization Guided KV Cache Compression](/202609/10/2609.03235v1-sgd-kv-summarization-guided-kv-cache-compression) （9.0/10）
4. [Random Attention: Rethinking KV Cache Eviction for Efficient Reasoning](/202609/10/2609.03430v1-random-attention-rethinking-kv-cache-eviction-for-efficient-reasoning) （9.0/10）
5. [GrowPage: On-Demand KV Budgeting for Efficient LLM Reasoning Serving](/202609/10/2609.03494v1-growpage-on-demand-kv-budgeting-for-efficient-llm-reasoning-serving) （9.0/10）
6. [What Matters for Aggressive Decoding-Time KV Eviction? Temporal Aggregation and Ranking Preservation](/202609/10/2609.03515v1-what-matters-for-aggressive-decoding-time-kv-eviction-temporal-aggregation-and-ranking-preservation) （9.0/10）
7. [VestigeKV: The NoPE-MLA KV Cache Carries Its Own Sparse-Attention Signal in a Vestigial Branch](/202609/10/2609.03949v2-vestigekv-the-nope-mla-kv-cache-carries-its-own-sparse-attention-signal-in-a-vestigial-branch) （9.0/10）
8. [Quality Recovery for Quantized KV Caches via Low-Rank Attention Adaptation](/202609/10/2609.04263v1-quality-recovery-for-quantized-kv-caches-via-low-rank-attention-adaptation) （9.0/10）
9. [BeaconKV: Key-Value Cache Compression Guided by Beacon Queries for Efficient Large Reasoning Model Inference](/202609/10/2609.04971v1-beaconkv-key-value-cache-compression-guided-by-beacon-queries-for-efficient-large-reasoning-model-inference) （9.0/10）
10. [ECOKV: Geometry-Aware KV Cache Eviction via Complementary Diversity Metrics](/202609/10/2609.06663v1-ecokv-geometry-aware-kv-cache-eviction-via-complementary-diversity-metrics) （9.0/10）
11. [CEDAR: Error-Bounded Residual Routing for Efficient Long-Context Attention](/202609/10/2609.07237v1-cedar-error-bounded-residual-routing-for-efficient-long-context-attention) （9.0/10）
12. [RouteRelay: Event-Triggered Cross-Layer Route Reuse for Efficient Dynamic Sparse Attention](/202609/10/2609.07306v1-routerelay-event-triggered-cross-layer-route-reuse-for-efficient-dynamic-sparse-attention) （9.0/10）
13. [MetaKV: Adaptive KV Cache Compression for Constrained LLM Inference](/202609/10/2609.07966v1-metakv-adaptive-kv-cache-compression-for-constrained-llm-inference) （9.0/10）
14. [Jacap: Robust KV Cache Eviction via Jacobian-Based Nonlinear Information Capacity Preservation](/202609/10/2609.08131v1-jacap-robust-kv-cache-eviction-via-jacobian-based-nonlinear-information-capacity-preservation) （9.0/10）
15. [Sample-Guided Exact Top-K Selection for Long-Context Sparse Attention](/202609/10/2609.08450v1-sample-guided-exact-top-k-selection-for-long-context-sparse-attention) （9.0/10）
16. [AMEND: Audited Margins Enable Nonblocking Drops in GPU-PIM LLM Decoding](/202609/10/2609.09823v1-amend-audited-margins-enable-nonblocking-drops-in-gpu-pim-llm-decoding) （9.0/10）

## 速读区
1. [Language Models Can Control Their Own Attention](/202609/10/2609.02737v1-language-models-can-control-their-own-attention) （8.0/10）
2. [Interface-Aware KV Cache Quantization for Dense On-Chip NVM in Long-Context LLM Decoding](/202609/10/2609.05764v1-interface-aware-kv-cache-quantization-for-dense-on-chip-nvm-in-long-context-llm-decoding) （8.0/10）
3. [Linear Algebra Foundations of Efficient Attention: A Phase Reversal in Rank Collapse Under SVD Compression](/202609/10/2609.06341v1-linear-algebra-foundations-of-efficient-attention-a-phase-reversal-in-rank-collapse-under-svd-compression) （8.0/10）
4. [RedKnot-MLA: Multi-Head Offline-Online Reuse for DeepSeek-V4 Long-Context Serving](/202609/10/2609.07008v1-redknot-mla-multi-head-offline-online-reuse-for-deepseek-v4-long-context-serving) （8.0/10）
5. [Graph Machine: Towards Better Pretraining via Edges](/202609/10/2609.02881v1-graph-machine-towards-better-pretraining-via-edges) （7.0/10）
6. [Dual-Latent Memory Routing for Vision-Language Reasoning](/202609/10/2609.05539v1-dual-latent-memory-routing-for-vision-language-reasoning) （7.0/10）
7. [CONDUIT: A Unified Residual-Stream Restoration Framework for KV Cache Reuse in Vision-Language Models](/202609/10/2609.05821v1-conduit-a-unified-residual-stream-restoration-framework-for-kv-cache-reuse-in-vision-language-models) （7.0/10）
8. [Query-Oblivious Coresets for Softmax Attention: Improved Bounds and Efficient Constructions](/202609/10/2609.06327v1-query-oblivious-coresets-for-softmax-attention-improved-bounds-and-efficient-constructions) （7.0/10）
9. [Modern Transformers Are Implicit Hybrids: From Functional Differentiation to Principled Hybrid Architecture Design](/202609/10/2609.02986v1-modern-transformers-are-implicit-hybrids-from-functional-differentiation-to-principled-hybrid-architecture-design) （6.0/10）
10. [Who Speaks for the Pruned? Visual Token Pruning as Coverage Optimization](/202609/10/2609.03158v1-who-speaks-for-the-pruned-visual-token-pruning-as-coverage-optimization) （6.0/10）
11. [Intra-Prompt Parallel Decoding for Common-Context Question Answering](/202609/10/2609.05707v1-intra-prompt-parallel-decoding-for-common-context-question-answering) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
