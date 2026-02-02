<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Detecting_Out_of_Distribution_Samples_via_Conditional_Distribution_Entropy_with_Optimal_Transport

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a novel OOD detection method based on Optimal Transport (OT). The core idea is to model OOD detection as a discrete optimal transport problem between the empirical distribution of training samples and the empirical distribution of test inputs. A key component is the proposed conditional distribution entropy score function, derived from the optimal transport plan. The method relies on feature representations, which can be obtained via supervised or self-supervised contrastive training.

The paper includes several ablation studies in Section 4.3:
1.  Effect of temperature (τ) in contrastive training.
2.  Effect of Contrastive Training (comparing SupCon vs. SupCE).
3.  Effect of Training Epochs.
4.  Effect of Regularization Coefficient (λ) in entropic regularized OT.
5.  Effect of Optimal Transport (comparing the full method with OT against a baseline without OT, which seems to degenerate to a distance-based method like KNN).

While the "Effect of Optimal Transport" ablation demonstrates the overall benefit of using OT, it doesn't fully explore the specific design choices *within* the OT framework itself. Two key aspects of setting up the discrete optimal transport problem are:
1.  **The cost matrix (C):** This matrix defines the cost of transporting mass between individual training and test features. The paper uses pairwise cosine distances between features, justified by normalizing features to a hypersphere. The choice of distance metric is crucial as it encodes the geometric relationship between samples, which OT leverages. An ablation studying the impact of using different distance metrics (e.g., Euclidean distance) in the cost matrix would be valuable.
2.  **The weights of the empirical distributions (µ and ν):** The paper uses uniform weights for both training and test samples. This assumes all samples contribute equally to their respective distributions. Exploring non-uniform weighting schemes (e.g., based on sample density or importance) could reveal whether certain samples are more critical for defining the ID/OOD distributions in the context of OT.

Based on this analysis, two important missing ablation studies are identified: one focusing on the distance metric used in the OT cost matrix and another on the uniform weighting of empirical distributions. These ablations would provide deeper insights into how the geometric and distributional assumptions encoded in the OT setup impact the OOD detection performance.

The suggested ablations are ranked by importance, with the distance metric being slightly more fundamental to the geometric nature of OT as presented.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Effect of Distance Metric in OT Cost
- **Ablated Part**: Distance metric used to construct the cost matrix C for Optimal Transport.
- **Action**: REPLACE
- **Replacement**: 
  - Euclidean distance
- **Metrics**: AUROC, AUPR, FPR95

### Effect of Empirical Distribution Weights
- **Ablated Part**: Uniform weights used for empirical probability measures µ and ν.
- **Action**: REPLACE
- **Replacement**: 
  - density-based weights
- **Metrics**: AUROC, AUPR, FPR95

</div>