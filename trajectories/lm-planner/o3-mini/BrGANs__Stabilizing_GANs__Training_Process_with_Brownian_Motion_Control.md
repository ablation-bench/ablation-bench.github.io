<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/BrGANs__Stabilizing_GANs__Training_Process_with_Brownian_Motion_Control

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper already demonstrates that using Brownian Motion Control (BMC) can stabilize GAN training. In the Dirac-GAN setting, BMC is applied to both generator and discriminator, while in normal GANs it is only imposed on the discriminator. One important missing study is to examine whether also applying BMC to the generator in normal GANs (or to both components simultaneously) provides further benefits in convergence speed and image quality. This experiment would help validate if incorporating controlled noise on the generator can better drive the whole system toward the desired equilibrium.

Another key ablation that is missing relates to the design choice of using Brownian motion (i.e. Gaussian-driven noise processes) for the controller. While theoretical guarantees are derived based on Brownian motion, it remains unexplored how alternative noise distributions (such as Lévy processes, Uniform noise, or Ornstein-Uhlenbeck noise) might affect overall stability and performance. This ablation would assess the sensitivity and robustness of the BMC to its underlying noise model, reporting standard metrics used in the paper like FID, inception score and convergence speed.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Dual-BMC for Normal GANs
- **Ablated Part**: Application of the BMC on the generator in normal GANs (currently only applied to the discriminator)
- **Action**: ADD
- **Replacement**: 
  - Apply BMC to the generator with a similar noise-based control law
  - Apply BMC to both generator and discriminator with varied controller strengths
- **Metrics**: FID, Inception Score, Convergence Iterations

### Alternative Noise Distributions in BMC
- **Ablated Part**: The type of stochastic noise used in the BMC mechanism
- **Action**: REPLACE
- **Replacement**: 
  - Lévy process based noise
  - Uniform noise
  - Ornstein-Uhlenbeck noise
- **Metrics**: FID, Inception Score, Convergence Speed

</div>