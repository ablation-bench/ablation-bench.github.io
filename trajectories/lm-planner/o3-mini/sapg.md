<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/sapg

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies to isolate the contribution of each key component of SAPG. First, we remove the off‐policy aggregation module so that the leader is updated only with its own on‐policy data; this will help quantify how much extra performance is gained from fusing off‐policy data from follower policies. Next, we test the effect of the aggregation scheme by replacing the leader–follower design with a symmetric scheme (or vice versa) to understand how the manner in which off‐policy data is integrated impacts learning. Third, we investigate the role of latent conditioning by ablating the shared backbone architecture: we compare using a shared backbone conditioned on local latent parameters versus completely independent network parameters per policy. Fourth, since the method employs entropy regularization on the followers to encourage exploration and diversify the trajectories, we propose removing the entropy bonus for followers to gauge its effect on exploration and final performance. Finally, we study the sensitivity of the off‐policy correction by replacing the current importance sampling formulation (with clipping) with variants (e.g. no clipping or a wider clipping range) to measure its impact on the stability and convergence of the updates.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Off-Policy Aggregation Removal
- **Ablated Part**: Data aggregation module that fuses off-policy data from follower policies into the leader update
- **Action**: REMOVE
- **Metrics**: Average Return, Sample Efficiency, Asymptotic Performance

### Aggregation Scheme Comparison
- **Ablated Part**: Aggregation strategy used to combine data from multiple policies (leader-follower vs. symmetric aggregation)
- **Action**: REPLACE
- **Replacement**: 
  - leader-follower aggregation
  - symmetric aggregation
- **Metrics**: Average Return, Sample Efficiency, Asymptotic Performance

### Latent Conditioning Ablation
- **Ablated Part**: Shared backbone with latent conditioning that enables communication between policies
- **Action**: REPLACE
- **Replacement**: 
  - shared backbone with latent conditioning
  - independent networks per policy
- **Metrics**: Average Return, Sample Efficiency, Asymptotic Performance

### Entropy Regularization Ablation
- **Ablated Part**: Entropy regularization on follower policies used to encourage diversity in exploration
- **Action**: REMOVE
- **Metrics**: Average Return, Policy Entropy, Exploration Diversity

### Importance Sampling Clipping Ablation
- **Ablated Part**: Off-policy update mechanism employing importance sampling with clipping for weighting transitions
- **Action**: REPLACE
- **Replacement**: 
  - clipped importance sampling (baseline)
  - no clipping
  - wider clipping range
- **Metrics**: Average Return, Stability, Convergence Speed

</div>