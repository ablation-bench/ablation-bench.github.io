<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/visualdet3d

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents a ground-aware monocular 3D object detection method with two main novel components:

1. Anchor Filtering - This filters out 3D anchors far from the ground plane during training and testing.

2. Ground-Aware Convolution (GAC) Module - This module:
- Encodes depth priors assuming pixels are on the ground
- Predicts vertical offsets to query features from contact points
- Merges features back with residual connections

The key metrics used in the paper are:
- 3D detection metrics (Easy/Moderate/Hard)
- BEV detection metrics (Easy/Moderate/Hard)
- Inference time

Based on this, I suggest the following ablation studies:

1. Remove anchor filtering to validate its importance
2. Remove the GAC module completely to test its overall impact
3. Test different components of the GAC module (depth priors, vertical offsets)
4. Test the post-optimization step
5. Replace the backbone with alternatives

These ablations target the key novel components while measuring impact on the main metrics used in the paper.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Anchor Filtering Ablation
- **Ablated Part**: Anchor filtering procedure that removes 3D anchors far from ground plane
- **Action**: REMOVE
- **Metrics**: 3D Easy, 3D Moderate, 3D Hard, BEV Easy, BEV Moderate, BEV Hard, Inference Time

### GAC Module Ablation
- **Ablated Part**: Complete Ground-Aware Convolution module
- **Action**: REMOVE
- **Metrics**: 3D Easy, 3D Moderate, 3D Hard, BEV Easy, BEV Moderate, BEV Hard, Inference Time

### GAC Components Ablation
- **Ablated Part**: Individual components of GAC module (depth priors and vertical offsets)
- **Action**: REPLACE
- **Replacement**: 
  - Only depth priors
  - Only vertical offsets
- **Metrics**: 3D Easy, 3D Moderate, 3D Hard, BEV Easy, BEV Moderate, BEV Hard

### Post-optimization Ablation
- **Ablated Part**: Post-optimization procedure for refining angle predictions
- **Action**: REMOVE
- **Metrics**: 3D Easy, 3D Moderate, 3D Hard, BEV Easy, BEV Moderate, BEV Hard, Inference Time

### Backbone Ablation
- **Ablated Part**: ResNet-101 backbone
- **Action**: REPLACE
- **Replacement**: 
  - ResNet-50
  - ResNet-34
- **Metrics**: 3D Easy, 3D Moderate, 3D Hard, BEV Easy, BEV Moderate, BEV Hard, Inference Time

</div>