<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/ipg

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Image Processing GNN: Breaking Rigidity in Super-Resolution" proposes IPG, a graph-based model for SR that aims to overcome the rigidity of traditional CNN and attention-based methods. The core ideas introduced to achieve this flexibility are:
1.  **Degree Flexibility**: Assigning variable node degrees based on a detail-rich indicator, rather than fixed degrees for all pixels/patches.
2.  **Pixel Node Flexibility**: Using pixels as graph nodes instead of larger patches to avoid misalignment issues.
3.  **Space Flexibility**: Constructing graphs by searching connections at both local and global scales.

Based on these key contributions highlighted by the authors, the most important ablation studies should investigate the impact of each of these flexible design choices on the model's performance.

1.  **Degree Flexibility Ablation**: The paper's primary argument is breaking "degree-equivalence rigidity". Ablating the variable degree assignment by replacing it with a fixed degree (like in traditional KNN graphs or implicitly in CNN/Attention) would directly test the importance of this core concept.
2.  **Space Flexibility Ablation**: The paper emphasizes the need for both local and global information and proposes specific sampling strategies for this. Ablating this by removing either the local or global graph component would demonstrate the contribution of each scale and the benefit of their combination.
3.  **Pixel Node Flexibility Ablation**: The choice of using pixels over patches is presented as crucial for avoiding misalignment in low-level vision tasks like SR. Replacing pixel nodes with patch nodes would test this claim and its impact on performance.

These three ablations cover the most significant deviations from previous rigid or less flexible graph-based SR methods discussed in the paper. They are ranked by their prominence in the paper's core argument, starting with degree flexibility. The standard metrics for Super-Resolution, PSNR and SSIM, which are implicitly used for comparison against SOTA in the paper, will be used to evaluate the impact of these ablations.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Fixed Degree
- **Ablated Part**: Variable node degree assignment based on detail-rich indicator
- **Action**: REPLACE
- **Replacement**: 
  - Fixed degree (uniform for all pixels)
- **Metrics**: PSNR, SSIM

### Ablation: Spatial Graph Strategy
- **Ablated Part**: Combination of local and global graph aggregation
- **Action**: REPLACE
- **Replacement**: 
  - Local graphs only
  - Global graphs only
- **Metrics**: PSNR, SSIM

### Ablation: Patch Nodes
- **Ablated Part**: Using pixels as graph nodes
- **Action**: REPLACE
- **Replacement**: 
  - Using image patches as graph nodes
- **Metrics**: PSNR, SSIM

</div>