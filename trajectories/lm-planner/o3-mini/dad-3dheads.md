<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/dad-3dheads

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose four key ablation studies targeting the most critical components of DAD-3DHeads and its associated DAD-3DNet model. First, we aim to assess the contributions of the Reprojection Loss component. This loss provides supervision for aligning the 3D mesh with the 2D image via orthographic projection, and its removal may hurt head pose estimation metrics (measured via Frobenius norm error and angular error) as well as the overall 3D reconstruction quality (median, mean, and standard deviation of error in mm). Second, we propose to remove the entire auxiliary 2D landmark prediction branch – including both the Gaussian heatmap loss and the direct landmark regression loss – to study how much its co-training supervision improves the reconstruction quality and landmark consistency (using metrics such as Reprojection NME and the quality score F_Q). Third, we suggest replacing the Fusion Module, which is based on multi-scale feature integration using BiFPN and an Inception module, with a simpler aggregation strategy (e.g. simple concatenation or a standard convolution block) to measure the impact of complex multi-scale fusion on both the 3D shape reconstruction (median/mean/std errors) and pose estimation accuracy. Finally, we propose to remove only the Gaussian Heatmap Loss while keeping the landmark regression branch. This ablation will help to isolate the role of the Gaussian formulation in guiding coarse landmark localization and its effect on overall landmark consistency and reconstruction accuracy.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Remove Reprojection Loss
- **Ablated Part**: Reprojection Loss in the objective function that aligns the projected 3D mesh with the input image
- **Action**: REMOVE
- **Metrics**: Frobenius norm error, Angle error (degrees), Median(mm), Mean(mm), Std(mm)

### Ablation 2: Remove Landmark Prediction Branch
- **Ablated Part**: Auxiliary 2D landmark prediction branch (including both landmark regression and Gaussian heatmap losses) that provides additional supervision
- **Action**: REMOVE
- **Metrics**: Reprojection NME, Annotation Consistency F_Q, Median(mm), Frobenius norm error

### Ablation 3: Replace Fusion Module
- **Ablated Part**: Fusion Module leveraging BiFPN and Inception-based multi-scale feature integration
- **Action**: REPLACE
- **Replacement**: 
  - simple concatenation
  - standard convolution block
- **Metrics**: Median(mm), Mean(mm), Std(mm), Frobenius norm error, Angle error (degrees), Reprojection NME

### Ablation 4: Remove Gaussian Heatmap Loss
- **Ablated Part**: Gaussian Heatmap Loss component used for guiding coarse landmark localization within the landmark branch
- **Action**: REMOVE
- **Metrics**: Reprojection NME, Annotation Consistency F_Q, Median(mm), Mean(mm), Std(mm)

</div>