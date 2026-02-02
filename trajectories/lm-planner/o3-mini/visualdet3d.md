<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/visualdet3d

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose four key ablation studies to understand the contribution and role of the ground plane priors incorporated in both the 3D detection and depth prediction tasks. First, since the ground‐aware convolution module is central to the approach (it encodes depth priors and adaptively aggregates features from ground pixels), its complete removal will reveal its overall benefit. Second, the anchor filtering step based on the ground plane is critical for focusing on physically plausible 3D proposals; removing it will test how much that spatial restriction aids detection. Third, within the ground-aware convolution module the network predicts dynamic vertical offsets to sample features from pixels below; replacing this dynamic mechanism with a fixed (or zero) offset baseline will isolate the gain from learning offsets. Fourth, the post-optimization step—using hill-climbing to refine the observation angle—is used to improve the final 3D box accuracy. Removing this step will help evaluate its role in balancing the multi-variable optimization. We report standard 3D detection metrics (e.g., 3D Moderate, BEV Moderate/Hard) and depth prediction metrics (SILog, absErrorRel, and iRMSE), as well as inference time where appropriate.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Ground-Aware Convolution Module
- **Ablated Part**: Ground-aware convolution module that extracts depth priors and aggregates features from ground pixels
- **Action**: REMOVE
- **Metrics**: 3D Detection (3D Moderate, BEV Moderate), Depth Prediction (SILog, absErrorRel, iRMSE)

### Ablation: Remove Ground-based Anchor Filtering
- **Ablated Part**: Anchor preprocessing that filters anchors based on their 3D position relative to the ground plane
- **Action**: REMOVE
- **Metrics**: 3D Detection (3D Moderate, BEV Moderate, 3D Hard), Inference Time

### Ablation: Replace Dynamic Offset with Fixed Offset
- **Ablated Part**: Dynamic offset prediction mechanism in the ground-aware convolution module used for sampling features below object centers
- **Action**: REPLACE
- **Replacement**: 
  - fixed offset computed from baseline geometry
  - zero offset
- **Metrics**: 3D Detection (3D Moderate, BEV Moderate), Depth Prediction (SILog, absErrorRel, iRMSE)

### Ablation: Remove Post-Optimization
- **Ablated Part**: The hill-climbing post-optimization step aimed at refining observation angle (and depth) estimates
- **Action**: REMOVE
- **Metrics**: 3D Detection (3D Moderate, 3D Hard), Inference Time

</div>