<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/memorizing-transformers-pytorch

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Memorizing Transformers" introduces a method to augment a standard decoder-only Transformer with a non-differentiable external memory accessed via approximate kNN lookup. This mechanism is integrated into one of the upper Transformer layers, combining attention over the local context with attention over retrieved memories using a learned gate. The core idea is to allow the model to "memorize" past inputs beyond the standard fixed context window, enabling rapid knowledge acquisition at inference time.

To understand the contribution of different components of this method, several ablation studies are crucial. I have identified five key areas for ablation, ranked by their importance in validating the core claims of the paper:

1.  **Ablating the entire kNN-augmented attention mechanism:** This is the most critical ablation. It directly tests whether the proposed memory mechanism, including the kNN lookup and integration into the attention layer, provides a benefit over a baseline Transformer (with Transformer-XL style local caching). Removing this component will show the overall performance gain attributable to the external memory system.
2.  **Investigating the combination strategy:** The paper uses a learned gate to combine the results of local attention and memory attention. Ablating this learned gate and replacing it with fixed combination strategies (like summation or averaging) will reveal if the learned weighting is important or if a simpler combination suffices. This helps understand how the model integrates information from the two sources.
3.  **Evaluating the impact of Query/Key Normalization:** The paper mentions normalizing keys and queries to mitigate distributional shift and staleness in the memory. Removing this normalization step will test its effectiveness in maintaining performance, especially with larger memory sizes.
4.  **Comparing Approximate vs. Exact kNN:** The paper uses approximate kNN for efficiency. While the primary goal is speed, it's important to verify if the approximation causes any performance degradation compared to using exact kNN (assuming computational resources allow for this comparison, at least on smaller scales).
5.  **Exploring the number of kNN-augmented layers:** The paper places the kNN-augmented attention in one layer near the top. Investigating whether adding this mechanism to multiple layers or placing it at different depths further improves performance can provide insights into the optimal architectural integration.

The primary metric used throughout the paper for evaluating language modeling performance is perplexity, measured across various datasets (C4, arXiv, PG-19, Github, Isabelle). Therefore, perplexity will be the main metric reported for these ablation studies.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No kNN-augmented Attention
- **Ablated Part**: The kNN-augmented attention mechanism (including kNN lookup and external memory access)
- **Action**: REMOVE
- **Metrics**: Perplexity

### Fixed Attention Combination
- **Ablated Part**: Learned gate for combining local and memory attention
- **Action**: REPLACE
- **Replacement**: 
  - Summation
  - Averaging
- **Metrics**: Perplexity

### No Query/Key Normalization
- **Ablated Part**: Normalization of queries and keys before kNN lookup
- **Action**: REMOVE
- **Metrics**: Perplexity

### Exact kNN Search
- **Ablated Part**: Approximate kNN search algorithm
- **Action**: REPLACE
- **Replacement**: 
  - Exact kNN Search
- **Metrics**: Perplexity

### Multiple kNN Layers
- **Ablated Part**: Number of kNN-augmented attention layers
- **Action**: ADD
- **Replacement**: 
  - Add kNN-augmented layers to other transformer blocks
- **Metrics**: Perplexity

</div>