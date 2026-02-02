<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/hdnet_tiktok

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper's methodology, there are several key components that warrant investigation through ablation studies:

1. The most critical component is the self-supervision mechanism using dance videos, which is a core novelty of the paper. Testing its effectiveness is crucial.

2. The joint learning of surface normals and depth is another key innovation that should be validated.

3. The part-based transformation using SE3 for warping is an important design choice that could be compared against alternatives.

4. The geometric consistency between predicted surface normals and derived surface normals is a key supervision signal.

5. The network architecture uses stacked hourglasses as backbone - this could be compared against alternatives.

I'll focus on the most important ablations that would validate the key claims and innovations of the paper. The metrics should align with those used in the paper: depth error, normal error, and reconstruction error.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Self-Supervision
- **Ablated Part**: Self-supervision loss from dance videos (Lw)
- **Action**: REMOVE
- **Metrics**: depth_error, normal_error, reconstruction_error

### Surface Normal Integration
- **Ablated Part**: Joint learning of surface normals and depth
- **Action**: REMOVE
- **Metrics**: depth_error, normal_error, reconstruction_error

### Transformation Model
- **Ablated Part**: SE3 transformation for part-based warping
- **Action**: REPLACE
- **Replacement**: 
  - affine_transformation
  - rigid_transformation
- **Metrics**: depth_error, normal_error, reconstruction_error

### Geometric Consistency
- **Ablated Part**: Geometric consistency loss between surface normals and depth (Ls)
- **Action**: REMOVE
- **Metrics**: depth_error, normal_error, reconstruction_error

</div>