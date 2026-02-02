<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/ssdnerf

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies to assess the key contributions of SSDNeRF. First, we remove the diffusion-based latent prior entirely from training to understand its role in stabilizing the latent codes and improving both generative and reconstruction quality. Second, we replace the single-stage joint optimization with a two-stage training paradigm (pretraining the NeRF auto-decoder and then training the diffusion model) to measure the benefit of end-to-end learning. Third, we investigate the sensitivity of the balancing mechanism between the rendering loss and the diffusion loss by replacing the dynamic, data‐dependent weighting with simpler constant weights. Fourth, we remove the test‐time guidance finetuning step, which refines the latent codes using rendering and diffusion losses, to quantify its impact on reconstruction fidelity. Finally, we remove the prior gradient caching strategy that accelerates finetuning, to evaluate its effect on training efficiency and overall reconstruction quality.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Diffusion Prior Removal
- **Ablated Part**: Diffusion-based latent prior guiding the NeRF auto-decoder
- **Action**: REMOVE
- **Metrics**: FID, KID, PSNR, SSIM, LPIPS

### Two-Stage Training Replacement
- **Ablated Part**: Joint optimization of NeRF auto-decoder and diffusion model (single-stage) vs. separate two-stage training
- **Action**: REPLACE
- **Replacement**: 
  - Two-Stage Training Paradigm
- **Metrics**: FID, KID, PSNR, SSIM, LPIPS

### Loss Weighting Sensitivity
- **Ablated Part**: The balancing mechanism between the rendering loss and diffusion loss
- **Action**: REPLACE
- **Replacement**: 
  - Dynamic Weighting (proposed)
  - Constant Weighting
- **Metrics**: FID, PSNR, SSIM, LPIPS

### Test-Time Guidance Finetuning Removal
- **Ablated Part**: Test-time finetuning step that refines latent codes using both rendering and diffusion losses
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, LPIPS

### Prior Gradient Caching Removal
- **Ablated Part**: Prior gradient caching mechanism used during finetuning to accelerate convergence
- **Action**: REMOVE
- **Metrics**: Training Efficiency, PSNR, SSIM

</div>