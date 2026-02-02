<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Pooling_And_Attention__What_Are_Effective_Designs_For_LLM_Based_Embedding_Models_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We note that the paper proposes a novel Multi-Layers Trainable Pooling method that leverages all hidden layers and incorporates a trainable layer weight matrix along with a cross-attention network to extract semantic information. However, two important components have not been individually ablated. First, while the paper shows performance improvements when using multi-layer information, it does not isolate the contribution of the trainable layer weight matrix. Removing this module and using a simple aggregation (e.g. averaging) over all layers would clarify how much of the boost in STS and retrieval tasks is due to the learned weighting rather than the mere inclusion of features from multiple layers. Second, although the analysis in Section 3.1 highlights that different layers capture distinct semantics, the method always pools from all layers. An ablation that replaces “all layers” with selected subsets (for example using only the last 4 layers or only the middle layers) would help determine if a smaller subset of layers might yield comparable—or even better—performance, thereby providing guidance on whether all layers are necessary.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Trainable Layer Weight Matrix
- **Ablated Part**: the trainable layer weight matrix within the Multi-Layers Trainable Pooling module
- **Action**: REMOVE
- **Metrics**: STS, Retrieval, Classification, Clustering

### Ablation: Selective Layer Inclusion for Pooling
- **Ablated Part**: the strategy of pooling from all hidden layers in the Multi-Layers Trainable Pooling module
- **Action**: REPLACE
- **Replacement**: 
  - all layers
  - last 4 layers
  - middle 4 layers
- **Metrics**: STS, Retrieval, Classification, Clustering

</div>