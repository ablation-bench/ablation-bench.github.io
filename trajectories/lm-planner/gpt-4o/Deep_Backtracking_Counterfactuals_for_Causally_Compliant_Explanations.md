<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Deep_Backtracking_Counterfactuals_for_Causally_Compliant_Explanations

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Deep Backtracking Counterfactuals for Causally Compliant Explanations" introduces a method for generating backtracking counterfactuals using deep generative models within structural causal models. The method is evaluated on datasets like Morpho-MNIST and CelebA, showcasing its ability to maintain causal compliance and modularity. The existing ablation studies in the paper focus on comparing the proposed method with interventional counterfactuals and other baselines, such as measuring distance in observable space and using incorrect causal graphs.

To suggest missing ablation studies, we need to identify key components of the method that have not been thoroughly evaluated. One potential area is the choice of distance functions used in the optimization problem. The paper mentions the flexibility of choosing different distance functions but does not explore how these choices impact the results. Another area is the penalty parameter λ used in the optimization, which is crucial for balancing the constraint satisfaction and the distance minimization. Exploring different values of λ could provide insights into the sensitivity and robustness of the method.

Therefore, the two missing ablation studies I suggest are: 
1. Ablating the choice of distance functions to understand their impact on the quality of counterfactuals.
2. Ablating the penalty parameter λ to evaluate its effect on the optimization process and the resulting counterfactuals.

These ablations will help in understanding the sensitivity of the method to these hyperparameters and provide insights into the robustness and flexibility of the proposed approach.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Distance Functions
- **Ablated Part**: choice of distance functions in the optimization problem
- **Action**: REPLACE
- **Replacement**: 
  - Euclidean
  - Manhattan
  - Cosine
- **Metrics**: plausible, obs, causal

### Ablation of Penalty Parameter
- **Ablated Part**: penalty parameter λ in the optimization
- **Action**: REPLACE
- **Replacement**: 
  - 0.1
  - 1
  - 10
  - 100
  - 1000
- **Metrics**: plausible, obs, causal

</div>