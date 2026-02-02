<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Seeing_the_Unseen__How_EMoE_Unveils_Bias_in_Text_to_Image_Diffusion_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that while the authors conducted several ablation studies (Section 4.4), there are still some important aspects of the EMoE framework that weren't fully investigated. Here's my reasoning for suggesting additional ablation studies:

1. The first missing ablation relates to the gating mechanism. The paper uses a specific approach for routing inputs to experts without training (described in Appendix D), but doesn't evaluate how this choice impacts the uncertainty estimation. This is crucial since the gating mechanism directly affects which experts handle each input.

2. The second important missing ablation concerns the choice of pre-trained experts. While the paper uses experts from different sources (Realistic Vision, Dreamlike Anime, Dreamshaper, etc.), it doesn't investigate how the diversity and number of experts affect the uncertainty estimation quality. This is particularly important since the paper claims that using pre-trained experts is a key advantage of their method.

For both ablations, we should use the same metrics as the paper - primarily the CLIP score correlation with uncertainty estimates, as this was the main evaluation metric used throughout the paper.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Gating Mechanism Ablation
- **Ablated Part**: The gating mechanism used for routing inputs to experts
- **Action**: REPLACE
- **Replacement**: 
  - Random routing
  - Equal weighting
  - Learned gating
- **Metrics**: CLIP score correlation with uncertainty, Generation time

### Expert Diversity Ablation
- **Ablated Part**: The selection and combination of pre-trained experts
- **Action**: REPLACE
- **Replacement**: 
  - All experts from same model family
  - Experts with similar training data
  - Experts with maximally different training data
- **Metrics**: CLIP score correlation with uncertainty, SSIM

</div>