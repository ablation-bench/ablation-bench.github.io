<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Align_Your_Intents__Offline_Imitation_Learning_via_Optimal_Transport

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The first missing ablation we propose is to remove the temporal lookahead term from the cost function. In AILOT the cost function (Eq. 10) not only computes the squared distance between the current intents but also adds a term comparing the lookahead (future) states. Although the paper discusses the necessity of ordering and temporal structure, it does not explicitly ablate this component. Removing the second term will quantify its contribution to the quality of the computed intrinsic rewards and downstream D4RL and sparse-reward performance.

The second missing ablation focuses on the choice of the distance metric used in the latent space. The authors use Euclidean distance as the measure for computing the cost between intent representations. However, OT methods can be sensitive to the underlying cost function. An ablation that replaces the Euclidean metric with Cosine or Manhattan distances would provide insight into how robust the method is to this design choice and whether an alternative metric might further improve alignment and performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Temporal Lookahead Ablation
- **Ablated Part**: The temporal lookahead component in the cost function that aligns future state intents (second term in Eq. 10)
- **Action**: REMOVE
- **Metrics**: Normalized D4RL locomotion scores, AntMaze scores

### Distance Metric Ablation
- **Ablated Part**: The distance function used in the latent intent space for optimal transport cost computation
- **Action**: REPLACE
- **Replacement**: 
  - Euclidean
  - Cosine
  - Manhattan
- **Metrics**: Normalized D4RL locomotion scores, Sparse-reward task scores, Learning convergence speed

</div>