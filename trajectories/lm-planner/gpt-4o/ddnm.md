<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/ddnm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The Denoising Diffusion Null-Space Model (DDNM) is a novel zero-shot framework for image restoration tasks that leverages a pre-trained diffusion model as a generative prior. The key innovation of DDNM is its ability to refine only the null-space contents during the reverse diffusion process, ensuring both data consistency and realness without additional training or network modifications. The enhanced version, DDNM+, further supports noisy restoration and improves restoration quality for challenging tasks.

To understand the impact of different components of the DDNM framework, we can propose several ablation studies. These studies will help attribute the performance of the method to its major components and understand the contribution of each part.

1. **Null-Space Refinement**: The core idea of DDNM is to refine only the null-space contents during the reverse diffusion process. An ablation study could involve removing this refinement step to see how it affects the model's ability to maintain data consistency and realness.

2. **Use of Pre-trained Diffusion Model**: DDNM relies on a pre-trained diffusion model as a generative prior. An ablation study could replace this with a different generative model or remove it entirely to assess its impact on the model's performance.

3. **Time-Travel Trick in DDNM+**: The time-travel trick is used to improve restoration quality by allowing the model to revisit previous states. An ablation study could involve removing this trick to evaluate its contribution to the overall performance.

4. **Scaling Range-Space Correction in DDNM+**: DDNM+ introduces scaling of the range-space correction to handle noisy image restoration. An ablation study could involve removing or altering this scaling to understand its role in supporting noisy restoration.

5. **Composite Degradation Handling**: DDNM is designed to handle complex IR tasks with composite degradation. An ablation study could involve testing the model's performance on individual degradation types to see how well it generalizes to composite tasks.

These ablation studies will be ranked by their importance based on the core contributions of the DDNM framework and its enhanced version, DDNM+.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Null-Space Refinement Ablation
- **Ablated Part**: Refinement of null-space contents during reverse diffusion
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, FID

### Pre-trained Diffusion Model Ablation
- **Ablated Part**: Use of pre-trained diffusion model as generative prior
- **Action**: REPLACE
- **Replacement**: 
  - GAN
  - VAE
- **Metrics**: PSNR, SSIM, FID

### Time-Travel Trick Ablation
- **Ablated Part**: Time-travel trick in DDNM+
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, FID

### Scaling Range-Space Correction Ablation
- **Ablated Part**: Scaling of range-space correction in DDNM+
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, FID

### Composite Degradation Handling Ablation
- **Ablated Part**: Handling of composite degradation tasks
- **Action**: REPLACE
- **Replacement**: 
  - Individual degradation types
- **Metrics**: PSNR, SSIM, FID

</div>