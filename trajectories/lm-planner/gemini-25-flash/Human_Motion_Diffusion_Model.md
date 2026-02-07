<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Human_Motion_Diffusion_Model

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Human Motion Diffusion Model" introduces MDM, a diffusion-based model for human motion generation. Key aspects of the method include a transformer-based architecture, predicting the clean sample (x̂₀) instead of the noise (ϵ), incorporating geometric losses, and using classifier-free guidance for conditioning (text or action).

The paper includes several ablation studies:
1.  **Backbone Architecture:** Comparing Transformer encoder (MDM's main architecture) with Transformer decoder variants, U-net, and GRU for text-to-motion (Table 1).
2.  **Text Encoder:** Comparing CLIP with sentence-BERT for text-to-motion (Table 1).
3.  **Guidance Scale:** Analyzing the effect of the classifier-free guidance scale 's' on text-to-motion performance (Figure 4b).
4.  **Number of Diffusion Steps (T):** Evaluating performance with different numbers of diffusion steps (Appendix A.1).
5.  **Geometric Losses:** Ablating different combinations of geometric losses (L_pos, L_vel, L_foot) on the Action-to-Motion task (HumanAct12 dataset) (Appendix A.2).

Based on the method description and existing ablations, two important missing ablation studies are:

1.  **Prediction Target:** The paper highlights predicting x̂₀ as a "notable design-choice" that facilitates geometric losses. However, they do not directly compare the performance of their x̂₀-prediction approach against the standard diffusion approach of predicting the noise ϵ. This comparison is crucial to validate the effectiveness of this core modification to the standard diffusion framework, especially since applying geometric losses might be challenging or impossible when predicting ϵ.
2.  **Geometric Losses on Text-to-Motion:** While geometric losses are ablated for the action-to-motion task (Appendix A.2), the paper explicitly states they are *not* applied for the text-to-motion task (Section 4.1 Implementation). Geometric properties are still relevant for text-to-motion quality. An ablation study evaluating the impact of these geometric losses on the text-to-motion task (e.g., on HumanML3D) is missing and would provide valuable insight into their general applicability and benefit across different conditioning types. The existing geometric loss ablation on action-to-motion was also quantitatively inconclusive, making a study on the primary text-to-motion task even more important.

These two ablations address fundamental design choices (prediction target) and key claimed benefits (geometric losses) in the context of the paper's main contributions (state-of-the-art text-to-motion).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Prediction Target Ablation
- **Ablated Part**: Diffusion model prediction target (clean sample x̂₀ vs. noise ϵ)
- **Action**: REPLACE
- **Replacement**: 
  - Predict noise (ϵ)
  - Predict clean sample (x̂₀)
- **Metrics**: R Precision (top 3)↑, FID↓, Multimodal Dist↓, Diversity→, Multimodality↑

### Geometric Losses Ablation (Text-to-Motion)
- **Ablated Part**: Geometric loss terms (L_pos, L_vel, L_foot)
- **Action**: REPLACE
- **Replacement**: 
  - None
  - L_pos only
  - L_vel only
  - L_foot only
  - L_pos + L_vel
  - L_pos + L_foot
  - L_vel + L_foot
  - L_pos + L_vel + L_foot
- **Metrics**: R Precision (top 3)↑, FID↓, Multimodal Dist↓, Diversity→, Multimodality↑

</div>