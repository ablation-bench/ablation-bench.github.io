<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Improving_Neuron_level_Interpretability_with_White_box_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The CRATE paper integrates two novel modules—the MSSA block and the ISTA‐overcomplete (sparse coding) block—to improve neuron-level interpretability by forcing representations to align with sparse, low-dimensional subspaces. Although the paper compares the overall CRATE architecture with GPT and even with GPT using post‐hoc sparse autoencoders, it does not individually ablate each major component to isolate their contributions. One important missing ablation is to remove (or replace) the built-in sparse coding mechanism provided by the ISTA block. Replacing this block with a standard MLP (as used in GPT) would help quantify the direct effect of enforcing sparsity explicitly on both the next-token prediction performance and neuron-level interpretability. A second key ablation is to replace the novel MSSA block with a standard multi-head self-attention mechanism (with separate Q, K, V projections and standard operations). This ablation would help determine if the compression leading to subspace alignment contributes meaningfully beyond the traditional attention mechanism. Both ablations would be evaluated on the paper’s metrics, for example, next-token prediction loss, OpenAI (top-and-random and random-only) interpretability metrics, Anthropic interpretability scores, and, optionally, activation sparsity measures.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Built-in Sparsification
- **Ablated Part**: ISTA-overcomplete block implementing built-in sparse coding in CRATE
- **Action**: REPLACE
- **Replacement**: 
  - Standard MLP block with ReLU activation
  - Standard FFN block
- **Metrics**: Next-token prediction loss, OpenAI Top-and-Random Interpretation Score, OpenAI Random-only Interpretation Score, Anthropic Interpretation Score, Activation sparsity

### Ablation: Replace MSSA Block
- **Ablated Part**: MSSA block (Multi-Head Subspace Self-Attention) used for compressing token representations
- **Action**: REPLACE
- **Replacement**: 
  - Standard multi-head self-attention with separate Q, K, V projections
- **Metrics**: Next-token prediction loss, Neuron-level interpretability (OpenAI and Anthropic metrics), Activation sparsity

</div>