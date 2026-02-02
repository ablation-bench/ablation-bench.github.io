<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/unsup3d

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies that target the most critical components of the paper’s method. The first ablation removes the symmetric branch (i.e. the flipped reconstruction of depth and albedo) which is central to enforcing the intrinsic symmetry assumption. The second ablation removes the confidence maps that allow the network to account for local asymmetries, especially in regions such as hair or other details. The third ablation replaces the explicit separation of albedo and lighting by using a combined, direct texture representation, testing whether the detailed modeling of illumination is beneficial. The fourth ablation removes the perceptual loss term, so that only the reconstruction L1 loss is used, which helps gauge its effect on sharpness and reconstruction fidelity. Finally, the fifth ablation investigates the impact of the balancing parameter (λf) that weights the symmetric branch loss by replacing its fixed value with several candidate weights. For each of these studies we report the performance in terms of metrics that are used in the paper such as Depth Correlation, SIDE (scaled inverse depth error), and MAD (Mean Angular Deviation). This ordered set of ablations should clarify the contribution of each component to the overall performance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Symmetric Branch
- **Ablated Part**: Symmetric reconstruction branch (flipping of depth and albedo maps to enforce bilateral symmetry)
- **Action**: REMOVE
- **Metrics**: Depth Corr, SIDE, MAD

### No Confidence Maps
- **Ablated Part**: Confidence maps that weight the reconstruction losses on regions where symmetry may fail
- **Action**: REMOVE
- **Metrics**: Depth Corr, SIDE, MAD

### Combined Texture Representation
- **Ablated Part**: Explicit lighting decomposition that separates albedo from illumination
- **Action**: REPLACE
- **Replacement**: 
  - direct texture representation
- **Metrics**: Depth Corr, SIDE, MAD

### No Perceptual Loss
- **Ablated Part**: Perceptual loss component used to improve reconstruction details
- **Action**: REMOVE
- **Metrics**: Depth Corr, SIDE, MAD

### Vary Symmetry Loss Weight
- **Ablated Part**: Weighting (λf) of the symmetric branch loss in the total reconstruction objective
- **Action**: REPLACE
- **Replacement**: 
  - 0
  - 0.25
  - 0.75
  - 1.0
- **Metrics**: Depth Corr, SIDE, MAD

</div>