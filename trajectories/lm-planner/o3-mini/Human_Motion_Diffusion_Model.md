<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Human_Motion_Diffusion_Model

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One key design choice in MDM is that it predicts the sample directly rather than the noise in each diffusion step. However, the paper does not report an ablation study comparing this choice against the canonical noise-prediction formulation. Evaluating this alternate formulation could help quantify its contribution to preserving motion geometry and overall generation quality. Additionally, the model is trained via classifier‐free guidance by randomly disabling conditioning for 10% of the samples during training. The effect of varying this masking ratio on fidelity and diversity of generated motions is not explored. Ablating the masking ratio may provide insights into the balance between condition adherence and sample diversity.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Prediction Target
- **Ablated Part**: The diffusion prediction target (predicting the sample rather than the noise)
- **Action**: REPLACE
- **Replacement**: 
  - Predicting noise
  - Predicting sample (baseline)
- **Metrics**: FID, R-Precision, Diversity, Multimodality

### Ablation: Classifier-Free Guidance Masking Ratio
- **Ablated Part**: The percentage of samples where the conditioning signal is masked (classifier-free guidance masking ratio)
- **Action**: REPLACE
- **Replacement**: 
  - 0%
  - 10% (baseline)
  - 20%
  - 30%
- **Metrics**: FID, R-Precision, Diversity, Multimodality

</div>