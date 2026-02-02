<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/deviant

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, DEVIANT's main contribution is using scale-equivariant steerable (SES) blocks to achieve depth equivariance in monocular 3D object detection. The key components that warrant ablation studies are:

1. The most critical ablation would be comparing the SES blocks against vanilla convolution blocks, since this is the core architectural innovation.

2. Testing different types of scale-equivariant approaches (SES vs LogPolar) is important since the paper claims SES is better.

3. The paper mentions that batch normalization and pooling layers should also be scale-equivariant for best performance, so this should be verified.

4. Since the method relies on the assumption of locally planar objects, testing different patch plane sizes would be valuable.

5. The number of scales used in the SES convolutions could impact performance and computational efficiency.

I'll rank these in order of importance and specify the exact ablations to perform.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Backbone Comparison
- **Ablated Part**: Scale-equivariant steerable (SES) backbone
- **Action**: REPLACE
- **Replacement**: 
  - Vanilla CNN backbone
  - LogPolar backbone
- **Metrics**: AP_3D, AP_BEV, AP_2D

### Scale-Equivariant Components
- **Ablated Part**: Scale-equivariant batch norm and pooling
- **Action**: REPLACE
- **Replacement**: 
  - Regular batch norm and pooling
  - Scale-equivariant batch norm only
  - Scale-equivariant pooling only
- **Metrics**: AP_3D, AP_BEV

### Number of Scales
- **Ablated Part**: Number of scales in SES convolutions
- **Action**: REPLACE
- **Replacement**: 
  - 1 scale
  - 2 scales
  - 4 scales
  - 8 scales
- **Metrics**: AP_3D, AP_BEV, Computational Time

### Patch Size
- **Ablated Part**: Local patch plane size for planar assumption
- **Action**: REPLACE
- **Replacement**: 
  - 4x4
  - 8x8
  - 16x16
  - 32x32
- **Metrics**: AP_3D, AP_BEV

### Scale Sampling
- **Ablated Part**: Scale sampling strategy in SES convolutions
- **Action**: REPLACE
- **Replacement**: 
  - Linear sampling
  - Logarithmic sampling
  - Exponential sampling
- **Metrics**: AP_3D, AP_BEV

</div>