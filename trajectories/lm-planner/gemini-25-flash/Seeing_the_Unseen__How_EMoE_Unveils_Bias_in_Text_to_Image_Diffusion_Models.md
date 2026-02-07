<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Seeing_the_Unseen__How_EMoE_Unveils_Bias_in_Text_to_Image_Diffusion_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Seeing the Unseen: How EMoE Unveils Bias in Text-to-Image Diffusion Models" proposes EMoE, a framework for estimating epistemic uncertainty in text-to-image diffusion models using pre-trained Mixture-of-Experts (MoE) networks. The core idea involves disentangling the expert components early in the diffusion process (specifically, at the first cross-attention layer in the first denoising step), extracting a latent representation after the mid-block (`m_post_0`) for each expert, and calculating the variance across these expert-specific latent representations as the measure of epistemic uncertainty. The framework leverages pre-trained models and an untrained gating mechanism.

The paper includes several ablation studies in Section 4.4:
1.  **Ensemble Size:** Investigates the effect of using 2, 3, or 4 experts.
2.  **Denoising Step:** Examines calculating uncertainty at different steps of the denoising process.
3.  **Latent Space:** Compares calculating uncertainty variance in different latent spaces (`Var(m_pre)`, `Var(m_post)`, `Var(z1)`).
4.  **Different MoE Model:** Tests EMoE's robustness on a different MoE architecture (Runway MoE).

While these ablations cover important aspects like the number of experts, the timing of the calculation, and the specific latent space, they leave some key design choices of EMoE unexplored. Two particularly important missing ablations relate to:

1.  **The specific location of expert disentangling:** The paper states that disentangling occurs at the *first cross-attention layer* in the first down block. This is a specific architectural choice for creating the separate expert paths. An ablation study could investigate if this specific early location is critical, or if disentangling at a different layer within the first denoising step (e.g., after the mid-block, closer to where `m_post_0` is extracted) yields similar or different results. This would test the importance of disentangling at the *very first* mixture layer versus a later one within the same initial step.
2.  **The role of the gating mechanism in uncertainty calculation:** The paper describes an untrained gating mechanism used in the standard MoE forward pass to select and weight experts. However, the uncertainty calculation (Equation 8) is defined as the variance across *all M* expert outputs (`Vari∈M`). Algorithm 1 also suggests processing *each* expert separately for the uncertainty calculation at the first step. This creates ambiguity about whether the gating mechanism (which typically selects a *subset* of experts) is actually applied to the expert outputs *before* calculating the variance for uncertainty estimation, or if all experts contribute equally. An ablation study comparing the current approach (variance across all experts, potentially influenced by gating weights if applied) with a simpler approach like uniform weighting of all expert outputs for the variance calculation would clarify the gating's contribution to the uncertainty estimate itself.

Based on this analysis, I propose the following two missing ablation studies, ranked by their importance in validating the core architectural and algorithmic choices of EMoE. Both ablations should use the metrics reported in the paper for evaluating uncertainty estimation quality: the correlation between uncertainty and image quality/prompt alignment, typically measured using CLIP score and SSIM across uncertainty quartiles.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Disentangling Location Ablation
- **Ablated Part**: Location within the first denoising step where expert outputs are disentangled to create separate computational paths for uncertainty estimation.
- **Action**: REPLACE
- **Replacement**: 
  - Disentangle at a later cross-attention layer within the first denoising step (e.g., after the mid-block)
  - Disentangle at a different type of layer within the first denoising step (e.g., first feed-forward layer)
- **Metrics**: CLIP Score, SSIM

### Gating Strategy for Uncertainty Ablation
- **Ablated Part**: The method used to combine or weight expert outputs when calculating the variance for epistemic uncertainty estimation.
- **Action**: REPLACE
- **Replacement**: 
  - Uniform weighting of all expert outputs (ignoring gating weights)
  - Using only the top-k experts selected by the gating mechanism
- **Metrics**: CLIP Score, SSIM

</div>