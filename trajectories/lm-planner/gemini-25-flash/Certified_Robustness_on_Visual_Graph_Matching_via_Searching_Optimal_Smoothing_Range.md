<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Certified_Robustness_on_Visual_Graph_Matching_via_Searching_Optimal_Smoothing_Range

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Certified Robustness on Visual Graph Matching via Searching Optimal Smoothing Range" proposes CR-OSRS, a method for providing certified robustness guarantees for visual graph matching. The method builds upon randomized smoothing but introduces several novel components to handle the specific challenges of visual GM, namely paired inputs, keypoint dependency, large permutation output space, and performance degradation from smoothing.

The key components of CR-OSRS include:
1.  Using a joint Gaussian distribution for smoothing noise to capture keypoint correlation.
2.  A global optimization algorithm to find optimal smoothing parameters (σ and correlation parameter b).
3.  Defining certified robustness based on the output falling into a subspace defined by similarity (s) to a core output (Xc), rather than certifying an exact output.
4.  Training strategies: Data augmentation with joint Gaussian noise and an output similarity-based regularization term.
5.  Methods for quantifying the certified space (Sampling and Marginal Radii).

The paper presents several ablation studies and analyses in Section 5 and Appendix E:
*   Comparison of CR-OSRS (with AUG+REG) against a modified RS-GM (isotropic Gaussian, with AUG+REG) (Table 1, Figures 2, 4, 5, 6, 7). This highlights the benefit of the joint distribution.
*   Ablation of training strategies (AUG and REG) by comparing CR-OSRS, CR-OSRS+AUG, and CR-OSRS+AUG+REG (Figures 2, 4, 5, 6, 7).
*   Hyperparameter analysis for σ, s, n, κ, β, and k (Figures 3, 8, 9, 10, 11).

Based on the method description and existing ablations, two important missing ablation studies are:

1.  **Ablation of the Core Output Definition:** The paper introduces a novel way to define the "core output" (Xc) by summing the output matrices from noisy samples and then applying Sinkhorn/Hungarian (Eq 4). This is a specific design choice to handle the large output space and computational complexity. An ablation study replacing this method with a common alternative, such as averaging the raw score/affinity matrices before applying Sinkhorn/Hungarian, would assess the impact of this specific aggregation strategy on certification performance. The paper justifies the chosen method based on computational efficiency, but its effect on the *quality* of the core output for certification is not explicitly studied against alternatives.

2.  **Ablation of the Global Optimization Strategy:** The paper proposes a global optimization algorithm (Alg 2, Eq 10) to find the optimal smoothing parameters (σ and b). While the paper analyzes the effect of varying σ and κ (related to b) in hyperparameter studies (Figures 3a, 9), it does not explicitly demonstrate the benefit of the *optimization process itself* compared to using fixed, non-optimized parameters. An ablation comparing the certified performance using parameters found by the global optimization versus using reasonable fixed parameters (e.g., initial values or values chosen from hyperparameter analysis) would quantify the contribution of this optimization strategy.

These two ablations target core novelties of the CR-OSRS method related to handling the output space and finding optimal smoothing parameters, respectively, and are not fully covered by the existing experiments. They are ranked by their perceived importance in validating the specific design choices made in CR-OSRS.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Core Output Definition Ablation
- **Ablated Part**: Method for determining the core output (Xc) from noisy samples
- **Action**: REPLACE
- **Replacement**: 
  - Average raw score/affinity matrices from noisy samples before applying Sinkhorn/Hungarian
- **Metrics**: Certified Accuracy (CA), Average Certified Radius (ACR), ∥δ∥lower, ∥δ∥upper, ∥δ∥volume

### Global Optimization Ablation
- **Ablated Part**: Global optimization algorithm for finding optimal smoothing parameters (σ, b)
- **Action**: REPLACE
- **Replacement**: 
  - Use fixed, pre-defined values for σ and b
- **Metrics**: Certified Accuracy (CA), Average Certified Radius (ACR), ∥δ∥lower, ∥δ∥upper, ∥δ∥volume

</div>