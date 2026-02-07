<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Pooling_And_Attention__What_Are_Effective_Designs_For_LLM_Based_Embedding_Models_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper conducts extensive ablation studies on different pooling and attention strategies, comparing:
1. EOS-Last Token Pooling + Causal Attention (Model 1)
2. Last-Layer Trainable Pooling + Causal Attention (Model 2) 
3. Multi-Layers Trainable Pooling + Causal Attention (Model 3)
4. Last-Layer Trainable Pooling + Bidirectional Attention (Model 4)
5. Multi-Layers Trainable Pooling + Bidirectional Attention (Model 5)

However, there are two important ablations missing:

1. Layer Selection Ablation: The paper proposes Multi-Layers Trainable Pooling which uses all layers, but doesn't investigate which specific layers contribute most to performance. This is important since using all layers increases computational cost.

2. Cross-Attention Architecture Ablation: The paper uses a cross-attention network with specific architecture choices (32 heads, 2048 channels) but doesn't justify these choices or explore alternatives. Understanding the impact of these architectural decisions is crucial.

I'll prioritize these two ablations since they directly relate to the paper's main contribution (Multi-Layers Trainable Pooling) and could provide valuable insights for practitioners implementing this method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Layer Selection Ablation
- **Ablated Part**: Layer selection in Multi-Layers Trainable Pooling
- **Action**: REPLACE
- **Replacement**: 
  - first_third_layers
  - middle_third_layers
  - last_third_layers
- **Metrics**: STS, Retrieval, Classification, Clustering

### Cross-Attention Architecture Ablation
- **Ablated Part**: Cross-attention network architecture in Multi-Layers Trainable Pooling
- **Action**: REPLACE
- **Replacement**: 
  - 8_heads_512_channels
  - 16_heads_1024_channels
  - 64_heads_4096_channels
- **Metrics**: STS, Retrieval, Classification, Clustering

</div>