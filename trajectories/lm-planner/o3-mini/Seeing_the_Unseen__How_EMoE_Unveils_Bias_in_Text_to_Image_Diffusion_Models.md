<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Seeing_the_Unseen__How_EMoE_Unveils_Bias_in_Text_to_Image_Diffusion_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We noticed that while the paper ablates several key design components – such as the optimal number of ensemble components, the choice of latent space for uncertainty estimation, the effect of the denoising step, and the use of a different MoE architecture (Runway MoE) – two areas remain unexplored. First, the paper does not study the impact of the dynamic gating module. The gating mechanism is used to assign weights to experts based on similarity between prompt activations and precomputed gate vectors. An ablation that replaces or removes this dynamic mechanism (for example, by using static equal weighting or a learned gating alternative) would help clarify how crucial this module is in capturing uncertainty and unveiling bias. Second, the method leverages inherent diversity by using pre-trained experts sourced from different repositories. However, it does not test the sensitivity of the method to expert diversity. It would be insightful to compare a heterogeneous ensemble (with pre-trained experts from different sources) against a homogeneous one (using identical copies of a single model) to understand the role of ensemble diversity in uncertainty estimation.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Gating Module Ablation
- **Ablated Part**: The dynamic gating mechanism used to weight each expert's contribution based on prompt similarity
- **Action**: REPLACE
- **Replacement**: 
  - Static equal weighting
  - Learned gating model
- **Metrics**: CLIP Score, Epistemic Uncertainty Correlation, SSIM

### Expert Diversity Ablation
- **Ablated Part**: The diversity of pre-trained experts integrated into the MoE framework
- **Action**: REPLACE
- **Replacement**: 
  - Heterogeneous experts from varied sources
  - Homogeneous experts (identical model instances)
- **Metrics**: CLIP Score, Variance of Expert Outputs, Epistemic Uncertainty Estimation

</div>