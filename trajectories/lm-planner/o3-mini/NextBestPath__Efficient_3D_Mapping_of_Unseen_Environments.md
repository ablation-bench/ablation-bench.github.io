<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/NextBestPath__Efficient_3D_Mapping_of_Unseen_Environments

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two missing ablation studies that further isolate key components of the NBP method. First, the mapping progress encoder aggregates two types of inputs: the 2D projections of the reconstructed point cloud and an image‐representation of the agent’s historical trajectory. The historical trajectory image helps the model discount previously visited regions, which is critical for efficient exploration. However, the paper does not evaluate the contribution of this cue. Removing this input will quantify its influence on the final reconstruction metrics (Final Cov. and AUCs). 

Second, the training procedure leverages a data augmentation strategy that exploits Dijkstra’s shortest path property to generate additional training samples from sub-path segments. Although this augmentation is likely to improve sample efficiency and prediction accuracy, its direct impact is not ablated. Removing this augmentation component will help to assess its role in the overall mapping performance. Both studies use the same evaluation metrics (Final Cov. and AUCs, as in the paper) to ensure consistency with prior experiments.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Historical Trajectory Input
- **Ablated Part**: Historical trajectory image used in the Mapping Progress Encoder to indicate previously visited regions
- **Action**: REMOVE
- **Metrics**: Final Cov., AUCs

### Ablation of Data Augmentation Strategy
- **Ablated Part**: Data augmentation by leveraging Dijkstra's sub-path property for expanding training samples
- **Action**: REMOVE
- **Metrics**: Final Cov., AUCs

</div>