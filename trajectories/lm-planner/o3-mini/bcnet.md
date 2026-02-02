<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/bcnet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies to analyze the contribution of key components in BCNet. The most critical innovation in BCNet is its bilayer formulation which decouples overlapping object boundaries via dual GCN layers – one for the occluder and one for the occludee. Removing or altering this key design will allow us to quantify its impact on instance segmentation performance, especially in heavy occlusion cases. In Ablation 1 we remove the entire bilayer structure and revert to a single GCN layer (thus not explicitly modeling occluder-occludee relationships). In Ablation 2, we remove the occlusion boundary supervision in the occluder branch which is used to learn precise boundary cues; this will help us understand its role in guiding occludee segmentation. Ablation 3 focuses on the residual fusion mechanism where the occluder’s features are added to the ROI features before the second GCN – by removing this connection, we assess its importance in forming occlusion-aware features. In Ablation 4 we replace the non-local operator within the GCN layers (which captures long-range relationships) with simpler alternatives (e.g., standard 3×3 convolution or local self-attention) to evaluate if global context aggregation is essential. Finally, Ablation 5 examines the effect of the occlusion sampling strategy used during training – currently balanced at 50% occluded proposals – by testing different ratios. For all experiments, we report standard instance segmentation metrics used in the paper such as mAP, AP50, AP75 and, where applicable, an occlusion-specific mAP.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Remove Bilayer Structure
- **Ablated Part**: Bilayer GCN structure that models occluder-occludee relationships
- **Action**: REMOVE
- **Metrics**: mAP, AP50, AP75, Occlusion mAP

### Ablation 2: Remove Occlusion Boundary Supervision
- **Ablated Part**: Boundary detection loss in the occluder branch
- **Action**: REMOVE
- **Metrics**: mAP, AP50, AP75

### Ablation 3: Remove Residual Fusion
- **Ablated Part**: Residual connection that fuses occluder features with ROI features before the second GCN
- **Action**: REMOVE
- **Metrics**: mAP, AP50, AP75

### Ablation 4: Replace Non-local Operator
- **Ablated Part**: Non-local operator used in the GCN layers for global context aggregation
- **Action**: REPLACE
- **Replacement**: 
  - 3x3 Standard Convolution
  - Local Self-Attention
- **Metrics**: mAP, AP50, AP75

### Ablation 5: Vary Occlusion Sampling Ratio
- **Ablated Part**: Occlusion-aware sampling strategy that balances occluded and non-occluded ROI proposals during training
- **Action**: REPLACE
- **Replacement**: 
  - Natural distribution
  - 30% occlusion
  - 50% occlusion
  - 70% occlusion
- **Metrics**: mAP, AP50, AP75

</div>