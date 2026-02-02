<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Implicit_Functional_Bayesian_Deep_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes two novel functional Bayesian deep learning approaches: implicit functional Bayesian neural networks (ifBNN) and implicit functional Bayesian deep ensembles (ifBDE). The key innovations are:

1. Using 2-Wasserstein distance instead of KL divergence for functional inference
2. Using neural tangent kernel (NTK) to transform BDL posterior to a Gaussian process
3. Introducing a Wasserstein barycenter approach for aggregating ensemble members

Looking at the existing ablations in the paper:
- They compare against baseline methods like FSVI, GWI, fBNN, etc.
- They evaluate on different tasks: regression, classification, contextual bandits
- They test different reward patterns in the contextual bandit task

However, there are two critical missing ablation studies:

1. The impact of the NTK-based GP transformation vs other possible transformations. This is a key technical contribution but its necessity is not validated.

2. The effect of using Wasserstein barycenter vs simple averaging for ensemble aggregation. While they propose using Wasserstein barycenter, they don't empirically validate its benefits over simpler approaches.

These ablations would help validate the key technical contributions and design choices of the method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### NTK Transformation Ablation
- **Ablated Part**: NTK-based GP transformation
- **Action**: REPLACE
- **Replacement**: 
  - Linear approximation transformation
  - Direct GP approximation without NTK
- **Metrics**: RMSE, NLL, OOD-AUC

### Ensemble Aggregation Ablation
- **Ablated Part**: Wasserstein barycenter aggregation
- **Action**: REPLACE
- **Replacement**: 
  - Simple averaging
  - Weighted averaging based on likelihood
- **Metrics**: RMSE, NLL, OOD-AUC

</div>