<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/ipg

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies that target the key innovations of the IPG model. First, the assignment of variable node degrees based on the detail-rich indicator is central to breaking the degree-rigidity of previous methods; removing this component will help isolate its contribution. Second, the design choice to use pixel nodes (instead of patch nodes) is critical to avoid misalignment issues. By replacing pixel nodes with patch-based representations (or even a hybrid), we can evaluate the impact of finer granularity on SR performance. Third, leveraging both local and global sampling strategies is a core part of the spatial flexibility strategy. Removing global sampling will show how much long-range interactions contribute to reconstruction quality. Fourth, the edge-conditioned aggregation is chosen for its ability to preserve inter-node relationships; replacing it with simpler aggregation functions (such as max-pooling or mean aggregation) can reveal its importance. Lastly, adding relative positional encoding aims to mitigate spatial information loss during aggregation. Removing this feature will clarify its role in maintaining effective spatial awareness. Each experiment will be measured using standard SR metrics (PSNR and SSIM) alongside complexity metrics (e.g., FLOPs) where appropriate.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Remove Degree Flexibility
- **Ablated Part**: Degree flexibility mechanism that assigns variable node degrees to pixels based on the detail-rich indicator
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, FLOPs

### Ablation 2: Replace Pixel Nodes with Patch Nodes
- **Ablated Part**: Node representation; using pixel-level nodes instead of traditional patch nodes for graph construction
- **Action**: REPLACE
- **Replacement**: 
  - patch nodes
  - hybrid (pixel + patch) nodes
- **Metrics**: PSNR, SSIM, FLOPs

### Ablation 3: Remove Global Graph Sampling
- **Ablated Part**: Global sampling strategy for constructing long-range connections in the image graph
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, FLOPs

### Ablation 4: Replace Edge-Conditioned Aggregation
- **Ablated Part**: Graph aggregation mechanism that leverages edge-conditioned filters
- **Action**: REPLACE
- **Replacement**: 
  - max-pooling
  - mean aggregation
- **Metrics**: PSNR, SSIM

### Ablation 5: Remove Relative Position Encoding
- **Ablated Part**: Relative positional encoding added to node features before aggregation to enhance spatial information
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM

</div>