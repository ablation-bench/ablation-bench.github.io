<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Improving_Neuron_level_Interpretability_with_White_box_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces CRATE, a white-box transformer architecture that embeds sparse coding directly into the model to improve neuron-level interpretability. The key components that enable this are:

1. The MSSA (Multi-Head Subspace Self-Attention) block which replaces standard attention
2. The ISTA (Iterative Shrinkage-Thresholding Algorithm) block which replaces the FFN block
3. The sparsification regularizer λ that controls the sparsity level

Looking at the ablations already present in the paper:
- They compare different model sizes (1L, 2L, 3L, 6L, 12L)
- They analyze activation sparsity across layers
- They compare against GPT-2 baseline and GPT-2 with post-hoc sparse autoencoders

Key missing ablations:

1. The sparsification regularizer λ is a critical hyperparameter that directly controls the sparsity-performance tradeoff, but there's no ablation studying its impact. We should test different values.

2. The MSSA block uses identical Q,K,V matrices unlike standard attention. While this is mentioned, there's no ablation showing the impact of this design choice versus using separate matrices like standard transformers.

These ablations would help attribute the model's interpretability gains to specific architectural choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Sparsification Regularizer Impact
- **Ablated Part**: sparsification regularizer λ in ISTA block
- **Action**: REPLACE
- **Replacement**: 
  - 0.05
  - 0.1
  - 0.2
- **Metrics**: interpretability score, next token prediction loss, activation sparsity

### MSSA Matrix Sharing
- **Ablated Part**: shared Q,K,V matrices in MSSA block
- **Action**: REPLACE
- **Replacement**: 
  - separate Q,K,V matrices like standard attention
- **Metrics**: interpretability score, next token prediction loss

</div>