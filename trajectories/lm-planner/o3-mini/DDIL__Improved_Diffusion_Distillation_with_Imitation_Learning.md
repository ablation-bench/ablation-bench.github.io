<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/DDIL__Improved_Diffusion_Distillation_with_Imitation_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

In our analysis of the DDIL paper, two key components in the DDIL framework have not been individually ablated. First, while the DDIL framework combines data distribution samples (forward diffusion), teacher backward trajectories, and student-induced backward trajectories to mitigate co-variate shift, the contribution of the student backward component is not independently evaluated. Removing this component would clarify how much it contributes to correcting the compounding error and improving the quality and diversity of the generated samples. Second, the method employs a fixed mixture ratio (sampling prior) among the three latent sources, yet there is no study on how different weighting configurations affect the DDIL’s performance. Testing alternative ratios could provide insight into balancing the preservation of marginal data distribution against correcting covariate shift. We propose two missing ablations that address these core aspects.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Student Backward Sampling
- **Ablated Part**: Inclusion of student induced backward trajectory sampling in the training distribution
- **Action**: REMOVE
- **Metrics**: FID, CLIP, LPIPSDiversity

### Ablation: Vary Sampling Prior Ratios
- **Ablated Part**: Fixed mixture ratios of forward diffusion, teacher backward, and student backward trajectory sampling
- **Action**: REPLACE
- **Replacement**: 
  - 50:25:25
  - 70:15:15
  - 30:35:35
  - 100:0:0
- **Metrics**: FID, CLIP, LPIPSDiversity

</div>