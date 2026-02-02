<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Latent_Trajectory_Learning_for_Limited_Timestamps_under_Distribution_Shift_over_Time

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper includes ablations on the maximum likelihood loss weight (α), the effect of varying temporal gaps (∆t), and comparisons between uni‐modal and multi‐modal classification losses. However, two important components of the proposed SDE-EDG method have not been directly ablated. First, the method relies on modeling evolving latent trajectories using stochastic differential equations (SDEs) that include an inherent diffusion (noise) component. It is critical to understand whether the stochasticity itself is beneficial; replacing the SDE with a deterministic counterpart (i.e. a Neural ODE by zeroing out the diffusion term) would help quantify its impact on capturing evolving patterns and generalization under distribution shifts. Second, IFGET is constructed by generating continuous‐interpolated samples via a linear interpolation function between matched samples across domains. Exploring alternative interpolation schemes (such as cubic or spline interpolation) would assess the sensitivity of the method to the choice of interpolation function and whether non‐linear interpolations might better capture subtle evolving dynamics.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: SDE vs. Deterministic ODE
- **Ablated Part**: Stochastic diffusion component in the SDE modeling of latent trajectories
- **Action**: REPLACE
- **Replacement**: 
  - Set diffusion term g(z, t) to 0 to obtain a deterministic (ODE-based) model
- **Metrics**: target domain accuracy, path alignment loss

### Ablation: Interpolation Function Variants
- **Ablated Part**: Interpolation function used for constructing the IFGET continuous trajectory
- **Action**: REPLACE
- **Replacement**: 
  - linear interpolation
  - cubic interpolation
  - spline interpolation
- **Metrics**: target domain accuracy, training convergence, J_mle

</div>