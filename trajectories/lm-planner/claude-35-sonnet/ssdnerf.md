<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/ssdnerf

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, SSDNeRF's main novelty lies in its single-stage training paradigm that jointly optimizes a NeRF auto-decoder and a latent diffusion model. The key components that deserve ablation studies are:

1. The single-stage training approach vs. two-stage training - this is the main technical contribution and should be validated.

2. The render-to-prior weight ratio balancing mechanism - the paper emphasizes its importance for generalization.

3. The prior gradient caching technique - introduced to accelerate training.

4. The SNR-based weighting function - used instead of LSGM's dual weighting mechanisms.

5. The guidance-finetuning sampling scheme - critical for test-time reconstruction.

I'll rank these by importance and formulate specific ablation experiments:
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Single vs Two-Stage Training
- **Ablated Part**: Single-stage training paradigm
- **Action**: REPLACE
- **Replacement**: 
  - Two-stage training (auto-decoder then diffusion)
  - Two-stage training with TV regularization
- **Metrics**: FID, KID, SSIM, LPIPS

### Weight Ratio Ablation
- **Ablated Part**: Render-to-prior weight ratio mechanism
- **Action**: REPLACE
- **Replacement**: 
  - Fixed ratio
  - Linear scaling with views
- **Metrics**: FID, KID, SSIM, LPIPS

### Gradient Caching
- **Ablated Part**: Prior gradient caching technique
- **Action**: REMOVE
- **Metrics**: Training time, FID, KID

### SNR Weighting
- **Ablated Part**: SNR-based weighting function
- **Action**: REPLACE
- **Replacement**: 
  - LSGM dual weighting
  - Constant weighting
- **Metrics**: FID, KID, SSIM

### Guidance-Finetuning
- **Ablated Part**: Test-time guidance-finetuning scheme
- **Action**: REPLACE
- **Replacement**: 
  - Only guidance without finetuning
  - Only finetuning without guidance
- **Metrics**: SSIM, LPIPS

</div>