<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Seer__Language_Instructed_Video_Prediction_with_Latent_Diffusion_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Seer: Language Instructed Video Prediction with Latent Diffusion Models" presents a novel approach to text-conditioned video prediction (TVP) using latent diffusion models. The authors propose a sample and computation-efficient model, named Seer, which leverages the prior knowledge embedded in pre-trained text-to-image (T2I) stable diffusion models along the temporal axis. Seer enhances the U-Net and language conditioning model by incorporating computation-efficient spatial-temporal attention and introduces a novel Frame Sequential Text Decomposer module that dissects a sentence's global instruction into temporally aligned sub-instructions.

To further evaluate the effectiveness of Seer, we suggest two missing ablation studies:

1. **Ablation Study 1: Impact of Spatial-Temporal Attention**
This study aims to investigate the effect of spatial-temporal attention on the performance of Seer. We propose to remove the spatial-temporal attention module and replace it with a simple concatenation of spatial and temporal features. This will help to understand the contribution of spatial-temporal attention in improving the video prediction quality.

2. **Ablation Study 2: Effectiveness of Frame Sequential Text Decomposer**
This study aims to evaluate the effectiveness of the Frame Sequential Text Decomposer module in improving the video prediction quality. We propose to remove the Frame Sequential Text Decomposer module and use a simple text encoder to generate a global instruction embedding. This will help to understand the contribution of the Frame Sequential Text Decomposer module in providing fine-grained guidance for video prediction.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Spatial-Temporal Attention
- **Action**: REMOVE
- **Metrics**: FVD, KVD

### Ablation Study 2
- **Ablated Part**: Frame Sequential Text Decomposer
- **Action**: REMOVE
- **Metrics**: FVD, KVD

</div>