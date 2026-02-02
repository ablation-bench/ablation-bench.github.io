<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/raydf

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies to isolate the contributions of the key components in RayDF. The highest priority study is to remove the multi-view consistency optimization module, which directly drives the network to yield geometry consistent across views—a central claim of the paper. Next, we remove the dual-ray visibility classifier from training to quantify its contribution to enforcing multi-view consistency. In addition, since the dual-ray classifier uses a symmetric design to better capture mutual visibility between rays, we suggest replacing it with a naive, non-symmetric (concatenation-based) variant in order to assess the importance of its careful design. We also propose a parameter study to vary the number of multi-view rays (M) used during the multi-view consistency optimization, as this number is set to 20 empirically and could affect both convergence and reconstruction quality. Finally, we study the effect of the surface normal-based outlier removal step––designed to remove inaccurately estimated points near sharp edges––by entirely removing this post-processing stage and testing its impact on final surface quality.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Remove Multi-View Consistency Optimization
- **Ablated Part**: Multi-view consistency optimization module that leverages multi-view rays and visibility scores to enforce geometric consistency
- **Action**: REMOVE
- **Metrics**: Chamfer Distance, F-score, Rendering Speed

### Ablation 2: Remove Dual-Ray Visibility Classifier
- **Ablated Part**: Dual-ray visibility classifier used to determine mutual visibility between rays for enforcing consistency
- **Action**: REMOVE
- **Metrics**: Chamfer Distance, F-score

### Ablation 3: Replace Dual-Ray Visibility Classifier with Naive Variant
- **Ablated Part**: Symmetric design of the dual-ray visibility classifier
- **Action**: REPLACE
- **Replacement**: 
  - Naive concatenation-based classifier
- **Metrics**: Classifier Accuracy, Chamfer Distance

### Ablation 4: Vary Number of Multi-View Rays (M)
- **Ablated Part**: Multi-view ray sampling parameter in the consistency optimization module
- **Action**: REPLACE
- **Replacement**: 
  - 10
  - 20
  - 40
- **Metrics**: Chamfer Distance, F-score, Training Convergence

### Ablation 5: Remove Surface Normal based Outlier Removal
- **Ablated Part**: Post-processing step that removes outlier points based on derived surface normal deviations
- **Action**: REMOVE
- **Metrics**: Chamfer Distance, Surface Smoothness

</div>