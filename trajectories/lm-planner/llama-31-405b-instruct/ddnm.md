<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/ddnm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

To design ablation studies for the Denoising Diffusion Null-Space Model (DDNM), we need to consider the key components of the method and how they contribute to its overall performance. The DDNM is a zero-shot solution for various image restoration tasks, including super-resolution, colorization, compressed sensing, inpainting, and deblurring.

One potential ablation study is to investigate the effect of the null-space refinement on the performance of the DDNM. This can be done by comparing the results of the DDNM with and without the null-space refinement step. Another potential ablation study is to examine the impact of the time-travel trick on the restoration quality. This can be done by comparing the results of the DDNM with and without the time-travel trick.

Additionally, we can also investigate the effect of the scaling range-space correction on the performance of the DDNM in handling noisy image restoration tasks. This can be done by comparing the results of the DDNM with and without the scaling range-space correction.

Finally, we can also examine the impact of the choice of the diffusion model on the performance of the DDNM. This can be done by comparing the results of the DDNM using different diffusion models, such as DDPM and DDIM.

Overall, the goal of these ablation studies is to understand the contribution of each component of the DDNM to its overall performance and to identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: null-space refinement
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, FID

### Ablation B
- **Ablated Part**: time-travel trick
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, FID

### Ablation C
- **Ablated Part**: scaling range-space correction
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, FID

### Ablation D
- **Ablated Part**: diffusion model
- **Action**: REPLACE
- **Replacement**: 
  - DDPM
  - DDIM
- **Metrics**: PSNR, SSIM, FID

### Ablation E
- **Ablated Part**: number of time steps
- **Action**: ADD
- **Replacement**: 
  - 10
  - 20
  - 30
- **Metrics**: PSNR, SSIM, FID

</div>