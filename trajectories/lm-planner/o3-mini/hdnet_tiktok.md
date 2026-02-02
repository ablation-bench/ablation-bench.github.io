<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/hdnet_tiktok

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The following ablation studies are designed to isolate and quantify the contributions of the key components in HDNet. First, we test the removal of the warping loss (Lw), which imposes temporal consistency via part‐based SE3 transformations between frames in the dance videos. This study will reveal how critical the self-supervised temporal supervision is for achieving high fidelity depth predictions. Second, we remove the joint learning of the surface normals (i.e. the geometric consistency loss Ls) so that the depth predictor works without the direct supervision provided by the normal estimates. This ablation will demonstrate whether the mutual supervision between depth and normals is essential for capturing fine fabric details and wrinkles. Third, we replace the part-based warping mechanism with a simplified global transformation (e.g., a global affine or global SE3 transformation) to investigate the importance of modeling local rigid movements with body part segmentation. Fourth, we remove the Siamese network structure by training on single frame inputs rather than paired frames from the video. This will help assess the benefit of using temporal pairs in self-supervision. All experiments will be evaluated on the same metrics as the paper: depth error (D. error), normal error (N. error), and reconstruction error (R. error).
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Warping Loss Removal
- **Ablated Part**: The self-supervised temporal warping module that enforces geometric consistency via part-based SE3 transformations
- **Action**: REMOVE
- **Metrics**: D. error, N. error, R. error

### Ablation 2: Joint Surface Normals Supervision Removal
- **Ablated Part**: The joint learning framework that enforces geometric consistency between predicted depths and surface normals
- **Action**: REMOVE
- **Metrics**: D. error, N. error, R. error

### Ablation 3: Global Transformation Replacement
- **Ablated Part**: The part-based warping mechanism used to map 3D geometry between frames
- **Action**: REPLACE
- **Replacement**: 
  - global affine transformation
  - global SE3 transformation
- **Metrics**: D. error, N. error, R. error

### Ablation 4: Siamese Network Removal
- **Ablated Part**: The Siamese network design that uses paired frames from dance videos for temporal self-supervision
- **Action**: REMOVE
- **Metrics**: D. error, N. error, R. error

</div>