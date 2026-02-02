<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/ddnm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, I'll suggest ablation studies focusing on the key components of DDNM:

1. The most important component is the null-space refinement during the reverse diffusion process. Testing without this would show its necessity.

2. The time-travel trick in DDNM+ is a crucial enhancement that improves restoration quality, especially for hard tasks. Testing different travel lengths would be valuable.

3. For noisy image restoration, DDNM+ uses scaling matrices (Σ_t and Φ_t) to handle noise. Testing without these or with different scaling strategies would demonstrate their importance.

4. The choice of pre-trained diffusion model could impact performance significantly. Testing with different models would show the method's robustness.

5. The pseudo-inverse operator A† construction method affects performance. Testing different construction approaches would be valuable.

The metrics used in the paper include PSNR (Peak Signal-to-Noise Ratio), SSIM (Structural Similarity Index), and FID (Fréchet Inception Distance) for evaluating image quality and restoration performance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Null-Space Refinement Ablation
- **Ablated Part**: null-space refinement during reverse diffusion
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, FID

### Time-Travel Length Study
- **Ablated Part**: time-travel length parameter l
- **Action**: REPLACE
- **Replacement**: 
  - 0
  - 1
  - 2
  - 5
  - 10
- **Metrics**: PSNR, SSIM, FID

### Noise Scaling Matrices
- **Ablated Part**: scaling matrices Σ_t and Φ_t in DDNM+
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, FID

### Diffusion Model Choice
- **Ablated Part**: pre-trained diffusion model
- **Action**: REPLACE
- **Replacement**: 
  - DDPM
  - DDIM
  - Score-based model
- **Metrics**: PSNR, SSIM, FID

### Pseudo-inverse Construction
- **Ablated Part**: pseudo-inverse operator construction method
- **Action**: REPLACE
- **Replacement**: 
  - SVD-based
  - Fourier-based
  - Hand-designed
- **Metrics**: PSNR, SSIM, FID

</div>