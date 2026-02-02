<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Human_Motion_Diffusion_Model

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Human Motion Diffusion Model" introduces a diffusion-based generative model for human motion data, leveraging a transformer-based architecture and geometric losses. The existing ablation studies in the paper focus on different backbones for the model, such as transformer encoder, decoder, GRU, and U-net, as well as the impact of different text encoders like CLIP and sentence-BERT. Additionally, the paper explores the effect of geometric losses on the model's performance.

To suggest missing ablation studies, we need to identify key components or design choices in the model that have not been thoroughly investigated. One notable design choice is the prediction of the sample itself rather than the noise in each diffusion step. This choice is crucial as it facilitates the use of geometric losses, which are important for maintaining the physical realism of the generated motions. Another aspect is the classifier-free guidance approach, which allows for trading off diversity and fidelity in the generated motions.

A potential missing ablation study could involve investigating the impact of predicting noise instead of the sample in each diffusion step. This would help understand the significance of the current design choice and its contribution to the model's performance. Another missing ablation could focus on the classifier-free guidance mechanism, specifically exploring the effect of varying the percentage of samples for which the condition is set to null during training. This would provide insights into the balance between diversity and fidelity in the generated motions.

These ablation studies would be important as they target fundamental design choices that could significantly influence the model's performance and its applicability to different motion generation tasks.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Prediction of sample instead of noise in each diffusion step
- **Action**: REPLACE
- **Replacement**: 
  - Predict noise instead of sample
- **Metrics**: R-precision, FID, Multimodal-Dist, Diversity, MultiModality

### Ablation Study 2
- **Ablated Part**: Classifier-free guidance percentage of null condition samples
- **Action**: REPLACE
- **Replacement**: 
  - 5
  - 10
  - 15
  - 20
- **Metrics**: R-precision, FID, Multimodal-Dist, Diversity, MultiModality

</div>