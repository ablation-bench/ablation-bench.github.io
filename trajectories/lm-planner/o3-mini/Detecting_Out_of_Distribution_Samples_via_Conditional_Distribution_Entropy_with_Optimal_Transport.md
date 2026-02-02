<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Detecting_Out_of_Distribution_Samples_via_Conditional_Distribution_Entropy_with_Optimal_Transport

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper already provides extensive ablations on temperature, contrastive training, training epochs, regularization coefficient, and the use of optimal transport. However, two key components remain underexplored. First, while the core novelty centers on the proposed conditional distribution entropy score function for OOD detection, the paper does not compare it directly against alternative entropy‐based scoring strategies (e.g. joint entropy, marginal entropy, or unconditioned entropy). Such an ablation would clarify whether the conditional aspect truly provides a performance gain. Second, the optimal transport framework relies on computing a cost matrix using cosine distance after feature normalization. The effect of this design choice is not studied; thus, experimenting with alternative distance metrics (for instance, Euclidean or Mahalanobis distances) could reveal the importance of the cost metric on overall OOD performance. These two missing ablation studies are critical to understanding the robustness and design choices of the method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Score Function Variant Ablation
- **Ablated Part**: Conditional distribution entropy score function used for OOD detection
- **Action**: REPLACE
- **Replacement**: 
  - joint entropy
  - marginal entropy
  - unconditioned entropy
- **Metrics**: AUROC, AUPR, FPR95

### Distance Metric Ablation for Cost Matrix
- **Ablated Part**: Cost matrix computation in the optimal transport formulation (cosine distance)
- **Action**: REPLACE
- **Replacement**: 
  - cosine distance
  - Euclidean distance
  - Mahalanobis distance
- **Metrics**: AUROC, AUPR, FPR95

</div>