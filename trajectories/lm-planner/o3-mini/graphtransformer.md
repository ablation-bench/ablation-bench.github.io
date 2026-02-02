<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/graphtransformer

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose four ablation studies that target the core contributions of the graph transformer architecture. The first ablation removes the Laplacian eigenvector-based positional encoding because it is a key novelty for encoding structural information in graphs and we would like to quantify its effect on performance. Next, we replace the batch normalization (used in our model) with the original layer normalization from standard transformers, allowing us to measure the impact of normalization on training convergence and generalization. Third, we remove the explicit edge feature injection—including its dedicated propagation pipeline—in order to assess how much the edge-specific modifications contribute, especially for tasks where edge attributes are critical. Finally, we replace the local neighborhood-restricted attention (which leverages the graph sparsity and connectivity structure) with a fully connected attention mechanism (or an alternative multi-hop variant) to evaluate how exploiting explicit graph connectivity affects efficiency and performance. These studies are ranked by importance based on the expected impact on the model’s generalization and task performance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Positional Encoding
- **Ablated Part**: Laplacian eigenvector-based positional encoding added to the initial node embeddings
- **Action**: REMOVE
- **Metrics**: accuracy, loss, convergence speed

### Ablation Normalization Scheme
- **Ablated Part**: Batch normalization used in transformer layers
- **Action**: REPLACE
- **Replacement**: 
  - Layer Normalization
- **Metrics**: accuracy, training time, generalization performance

### Ablation Edge Feature Injection
- **Ablated Part**: Explicit edge feature multiplication in attention scores and its dedicated edge feature pipeline
- **Action**: REMOVE
- **Metrics**: accuracy, AUC, F1 score

### Ablation Attention Connectivity
- **Ablated Part**: Local neighborhood connectivity restriction in the attention mechanism
- **Action**: REPLACE
- **Replacement**: 
  - Fully Connected Attention
  - 2-hop Neighborhood Attention
- **Metrics**: accuracy, computational cost, memory usage

</div>