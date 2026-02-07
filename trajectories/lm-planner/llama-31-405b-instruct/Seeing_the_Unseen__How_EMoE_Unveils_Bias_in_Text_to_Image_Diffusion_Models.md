<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Seeing_the_Unseen__How_EMoE_Unveils_Bias_in_Text_to_Image_Diffusion_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Seeing the Unseen: How EMoE Unveils Bias in Text-to-Image Diffusion Models" presents a novel framework called Epistemic Mixture of Experts (EMoE) for estimating epistemic uncertainty in text-to-image diffusion models. The authors propose two ablation studies to further investigate the effectiveness of their approach.

The first ablation study could involve removing the disentanglement of the expert components in the first cross-attention layer. This would help to understand the importance of disentangling the experts in capturing epistemic uncertainty. The action would be to REMOVE the disentanglement step, and the metrics to report would be the CLIP score and uncertainty estimates.

The second ablation study could involve replacing the latent space used for uncertainty estimation. The authors use the variance of the mid-block latent representation (m_post) as their uncertainty estimate. An alternative approach could be to use the variance of the output of the U-Net (z_0) as the uncertainty estimate. The action would be to REPLACE the latent space used for uncertainty estimation, and the metrics to report would be the CLIP score and uncertainty estimates.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Disentanglement of expert components
- **Action**: REMOVE
- **Metrics**: CLIP score, Uncertainty estimates

### Ablation 2
- **Ablated Part**: Latent space for uncertainty estimation
- **Action**: REPLACE
- **Replacement**: 
  - Variance of U-Net output (z_0)
- **Metrics**: CLIP score, Uncertainty estimates

</div>