<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Improving_Neuron_level_Interpretability_with_White_box_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Improving Neuron-level Interpretability with White-box Language Models" introduces the CRATE model, which integrates sparse coding directly into the model architecture to enhance neuron-level interpretability. The paper already includes several ablation studies, such as comparing CRATE with GPT and GPT with post-hoc sparse auto-encoders. However, there are still some potential ablation studies that could provide further insights into the model's performance and interpretability.

One missing ablation study could involve the removal of the Multi-Head Subspace Self-Attention (MSSA) block. The MSSA block is a key component of the CRATE model, responsible for compressing token representations. By removing this block, we can assess its impact on the model's interpretability and performance. This ablation would help determine the importance of the MSSA block in achieving the reported improvements in neuron-level interpretability.

Another potential ablation study could involve replacing the Iterative Shrinkage-Thresholding Algorithm (ISTA) block with a standard MLP block, similar to the one used in GPT models. The ISTA block is designed to encourage sparsity in the token representations, which is a central aspect of the CRATE model's design. By replacing it with a standard MLP block, we can evaluate the effect of the sparsity-inducing mechanism on the model's interpretability and performance. This ablation would provide insights into the trade-offs between sparsity and interpretability.

Both of these ablation studies would use the same interpretability metrics as the original paper, such as the OpenAI top-and-random, random-only, and Anthropic metrics, to ensure consistency in the evaluation of interpretability.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Multi-Head Subspace Self-Attention (MSSA) block
- **Action**: REMOVE
- **Metrics**: OpenAI top-and-random, OpenAI random-only, Anthropic

### Ablation Study 2
- **Ablated Part**: Iterative Shrinkage-Thresholding Algorithm (ISTA) block
- **Action**: REPLACE
- **Replacement**: 
  - Standard MLP block
- **Metrics**: OpenAI top-and-random, OpenAI random-only, Anthropic

</div>