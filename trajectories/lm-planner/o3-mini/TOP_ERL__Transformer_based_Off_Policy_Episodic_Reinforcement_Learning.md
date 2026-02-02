<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/TOP_ERL__Transformer_based_Off_Policy_Episodic_Reinforcement_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two additional ablation studies that are missing from the paper. First, TOP-ERL uses a full covariance matrix for the Gaussian policy over movement primitive parameters in order to capture inter-dimensional correlations of the trajectories. However, the paper does not analyze the impact of this specific design choice. By replacing the full covariance with a simpler diagonal covariance matrix, one can evaluate the trade-off between expressive power and computational complexity, and assess its effects on sample efficiency, training stability, and overall success rates in dense and sparse reward environments.
Second, the method leverages ProDMPs as the trajectory generator to enforce initial conditions via a closed‐form solution. Although this mechanism is crucial for matching state-action consistency in computing the N‐step return, the paper does not compare it against a more conventional trajectory generator — for example, using a standard DMP formulation that requires numerical integration. Such an ablation would isolate the benefits of the closed-form ProDMP formulation for bias reduction in target computation and its influence on learning performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Covariance Structure in Gaussian Policy
- **Ablated Part**: Full covariance matrix in the Gaussian policy used to parameterize movement primitives
- **Action**: REPLACE
- **Replacement**: 
  - diagonal covariance
- **Metrics**: success_rate_dense, success_rate_sparse, sample_efficiency, training_stability

### Ablation 2: Movement Primitive Generator Type
- **Ablated Part**: ProDMP-based trajectory generator used to enforce initial condition consistency
- **Action**: REPLACE
- **Replacement**: 
  - standard DMP
- **Metrics**: task_success_rate, sample_efficiency, policy_stability

</div>