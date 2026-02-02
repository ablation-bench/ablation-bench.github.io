<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/deviant

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five targeted ablation studies to isolate the impact of key components in DEVIANT. The most critical aspect of our method is the incorporation of depth equivariance via scale‐equivariant steerable blocks. Thus, our first ablation is to replace these steerable blocks with standard vanilla convolutions, which quantifies the benefits brought by modeling depth translations. Next, the paper also modifies BatchNorm and pooling layers to operate over the extra (scale) dimension – we therefore propose replacing the equivariant BN and pooling layers with their vanilla counterparts to understand their contribution. A third study targets the MaxScale aggregation layer that projects the five-dimensional output back to four dimensions; by substituting it with alternative aggregation methods (e.g., average pooling or bypassing pooling), we can assess its role in preserving equivariance. In a fourth experiment, we test an alternative approach by replacing the steerable blocks with log-polar convolution to evaluate if the discretization issues discussed in the paper affect performance. Finally, we propose to vary the number of scales used in the steerable blocks (e.g., using 3, 5, or 7 scales) to gauge the sensitivity of the backbone to this parameter. In all cases, we will report detection performance metrics (AP_3D, AP_BEV, AP_2D) and additional depth quality metrics (e.g., Abs Rel, RMSE, and SSIM for the log-polar variant), which are commonly used in the paper.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Vanilla Convolution Ablation
- **Ablated Part**: Depth-equivariant steerable blocks
- **Action**: REPLACE
- **Replacement**: 
  - vanilla convolution blocks
- **Metrics**: AP_3D, AP_BEV, AP_2D, Abs Rel, RMSE

### BN and Pooling Ablation
- **Ablated Part**: Equivariant BatchNorm and pooling layers
- **Action**: REPLACE
- **Replacement**: 
  - vanilla BatchNorm
  - vanilla pooling
- **Metrics**: AP_3D, AP_BEV, AP_2D, RMSE

### MaxScale Aggregation Ablation
- **Ablated Part**: MaxScale layer for aggregating the scale dimension
- **Action**: REPLACE
- **Replacement**: 
  - average pooling over scale
  - no pooling (concatenation)
- **Metrics**: AP_3D, AP_BEV

### LogPolar Convolution Ablation
- **Ablated Part**: Scale-equivariant steerable blocks
- **Action**: REPLACE
- **Replacement**: 
  - log-polar convolution
- **Metrics**: AP_3D, SSIM

### Steerable Block Scale Variation
- **Ablated Part**: Number of scales in steerable blocks
- **Action**: REPLACE
- **Replacement**: 
  - 3 scales
  - 5 scales
  - 7 scales
- **Metrics**: AP_3D, AP_BEV, AP_2D

</div>