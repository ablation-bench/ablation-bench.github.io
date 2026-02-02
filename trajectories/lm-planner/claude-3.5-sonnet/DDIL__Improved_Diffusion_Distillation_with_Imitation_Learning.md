<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/DDIL__Improved_Diffusion_Distillation_with_Imitation_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that while the authors present several experiments comparing their method with baselines, there are some important ablations missing that could help better understand the contribution of key components:

1. The paper introduces two main components:
- Training on both data distribution (forward diffusion) and student-induced distributions (backward diffusion)
- Using reflected diffusion formulation for distillation

2. The existing ablations show:
- Comparisons against baselines (PD, LCM, DMD2)
- Performance with different number of steps
- Impact of batch size

3. Key missing ablations:
1) The most critical missing ablation is on the sampling priors (βfrwd, βteach_bckwrd, βstudent_bckwrd) which control the mix of forward and backward trajectories during training. The paper mentions these are important but doesn't ablate their values or study their individual impact.

2) The reflected diffusion component is presented as important for stability but there's no systematic study of different thresholding values and their impact on both training stability and final performance.

I'll focus on these two as they represent core contributions that lack proper ablation studies.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Sampling Priors Ablation
- **Ablated Part**: Sampling prior weights (βfrwd, βteach_bckwrd, βstudent_bckwrd) that control the mix of forward and backward trajectories
- **Action**: REPLACE
- **Replacement**: 
  - (0.8, 0.1, 0.1)
  - (0.6, 0.2, 0.2)
  - (0.4, 0.3, 0.3)
  - (0.33, 0.33, 0.33)
- **Metrics**: FID, CLIP score, LPIPSDiversity

### Reflected Diffusion Thresholds
- **Ablated Part**: Thresholding values used in the reflected diffusion formulation
- **Action**: REPLACE
- **Replacement**: 
  - 0.1
  - 0.5
  - 1.0
  - 2.0
- **Metrics**: FID, CLIP score, Training stability measure

</div>