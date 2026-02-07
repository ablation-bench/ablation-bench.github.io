<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/DDIL__Improved_Diffusion_Distillation_with_Imitation_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "DDIL: Improved Diffusion Distillation with Imitation Learning" proposes a novel framework for diffusion distillation that addresses covariate shift by training the student model on a mixture of data distributions (forward diffusion) and student/teacher induced distributions (backward trajectories), inspired by the DAgger algorithm. Additionally, the paper incorporates reflected diffusion (thresholding) to improve training stability.

The paper presents experimental results comparing baseline distillation methods (Progressive Distillation, LCM, DMD2) with versions augmented by DDIL (`+DDIL`) and versions augmented by both reflected diffusion and DDIL (`+Reflected +DDIL`). These comparisons implicitly serve as ablations for the *presence* of the DDIL mixing strategy (comparing Baseline vs Baseline + DDIL) and the *presence* of reflected diffusion (comparing Baseline + DDIL vs Baseline + Reflected + DDIL).

However, the paper does not provide ablation studies on key hyperparameters and design choices within the proposed DDIL framework and the reflected diffusion component. Specifically, two important missing ablations are:

1.  **The mixing strategy/priors (βf rwd, βteach\_bckwrd, βstudent\_bckwrd):** The core of DDIL is sampling training data from a mix of forward diffusion, student backward, and teacher backward trajectories, controlled by these priors. The paper mentions these priors and a dynamic schedule based on training progress but does not show experiments varying these ratios or schedules. Understanding how different mixing proportions impact performance (quality, diversity, stability) is crucial for validating this core mechanism.
2.  **The specific application of thresholding in Reflected Diffusion:** The paper states that thresholding is applied to the teacher's estimates consistently and to the student's target/critic where applicable. However, it doesn't show experiments isolating the effect of thresholding only the teacher, only the student, or both. This ablation would clarify which component's thresholding is most beneficial for stability and performance.

Based on this analysis, I propose two missing ablation studies focusing on these aspects. The metrics used in the proposed ablations are the same as those reported in the paper's main results tables (FID, CLIP, LPIPS Diversity, and HPSv2 where applicable, though I will list the common ones).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### DDIL Sampling Prior Analysis
- **Ablated Part**: The mixing strategy/priors (beta_forward, beta_teacher_backward, beta_student_backward) for sampling training data sources.
- **Action**: REPLACE
- **Replacement**: 
  - Fixed ratio (e.g., 100% forward)
  - Fixed ratio (e.g., 100% student backward)
  - Fixed ratio (e.g., 50% forward, 50% student backward)
  - Different dynamic schedules for priors
- **Metrics**: FID, CLIP, LPIPS Diversity

### Reflected Diffusion Component Ablation
- **Ablated Part**: Application of thresholding (reflected diffusion) to different model outputs (teacher, student target/output, critic).
- **Action**: REPLACE
- **Replacement**: 
  - No thresholding
  - Thresholding Teacher only
  - Thresholding Student target/output only
  - Thresholding Both Teacher and Student
- **Metrics**: FID, CLIP, LPIPS Diversity

</div>