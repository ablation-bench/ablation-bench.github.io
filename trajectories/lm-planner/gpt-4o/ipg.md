<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/ipg

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces the Image Processing GNN (IPG) model, which leverages graph flexibility to improve super-resolution (SR) tasks by addressing the rigidity of traditional CNN and window-attention methods. The key components of the IPG model include degree flexibility, pixel node flexibility, and space flexibility. These components are designed to handle the unbalanced nature of SR tasks, where detail-rich regions require more reconstruction effort than flat regions.

1. **Degree Flexibility**: The model assigns higher node degrees to detail-rich image nodes, which is a novel approach to address the unbalanced nature of SR tasks. An ablation study could investigate the impact of this degree flexibility by removing or altering the degree assignment strategy.

2. **Pixel Node Flexibility**: Unlike previous methods that use patches as nodes, IPG uses individual pixels as nodes to avoid misalignment issues. An ablation study could explore the effect of using patch nodes instead of pixel nodes.

3. **Space Flexibility**: The model constructs both local and global graphs to gather information from different scales. An ablation study could examine the impact of using only local or only global graphs.

4. **Graph Aggregation Method**: The IPG model uses edge-conditioned aggregation, which is crucial for maintaining neighboring information. An ablation study could replace this with max-pooling to see how it affects performance.

5. **Detail-Rich Indicator**: The detail-rich indicator is used to assign node degrees. An ablation study could replace this indicator with a simpler metric to evaluate its importance.

The metrics to report in these ablation studies should include those used in the paper, such as PSNR (Peak Signal-to-Noise Ratio) and SSIM (Structural Similarity Index), which are standard for evaluating SR performance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Degree Flexibility
- **Ablated Part**: Degree assignment strategy based on detail-rich indicator
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM

### Ablation 2: Pixel Node Flexibility
- **Ablated Part**: Use of pixel nodes instead of patch nodes
- **Action**: REPLACE
- **Replacement**: 
  - patch nodes
- **Metrics**: PSNR, SSIM

### Ablation 3: Space Flexibility
- **Ablated Part**: Use of both local and global graphs
- **Action**: REPLACE
- **Replacement**: 
  - only local graphs
  - only global graphs
- **Metrics**: PSNR, SSIM

### Ablation 4: Graph Aggregation Method
- **Ablated Part**: Edge-conditioned aggregation
- **Action**: REPLACE
- **Replacement**: 
  - max-pooling
- **Metrics**: PSNR, SSIM

### Ablation 5: Detail-Rich Indicator
- **Ablated Part**: Detail-rich indicator for node degree assignment
- **Action**: REPLACE
- **Replacement**: 
  - simple gradient-based metric
- **Metrics**: PSNR, SSIM

</div>