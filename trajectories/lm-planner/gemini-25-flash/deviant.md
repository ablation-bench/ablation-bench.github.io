<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/deviant

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants a list of up to 5 important ablation studies for the paper "DEVIANT: Depth EquiVarIAnt NeTwork for Monocular 3D Object Detection". The goal is to understand which components of the proposed method contribute most to its performance.

The core contribution of DEVIANT is the use of Scale Equivariant Steerable (SES) blocks in the backbone to achieve depth equivariance in the projective manifold, contrasting with standard vanilla CNNs which are only 2D translation equivariant.

Based on the paper's description, the key components and design choices are:
1.  **The use of SES blocks:** This is the central idea for achieving depth equivariance. Replacing this with a standard vanilla CNN backbone is the most critical ablation to verify the overall hypothesis.
2.  **Handling the extra scale dimension:** SES convolutions output 5D tensors. The paper uses 3D pooling and 3D Batch Normalization (BN), followed by a MaxScale layer. The choice of 3D BN/Pool is mentioned as important in Section 4 and confirmed in Section 6.1. Ablating this specific choice (e.g., comparing 3D vs 2D BN/Pool) is relevant.
3.  **Choice of scale-equivariant method:** The paper discusses Log-Polar convolutions as an alternative scale-equivariant approach but argues against it due to discretization issues. A direct ablation comparing SES with Log-Polar would empirically validate this claim within the 3D detection context.
4.  **The MaxScale layer:** This layer reduces the 5D tensor to 4D. While important, ablating the specific reduction strategy (max pooling over scale) might be less impactful than the choice of the equivariant block itself or the BN/Pool type.

Prioritizing these, the most important ablations are:
1.  Replacing the entire SES backbone with a vanilla CNN backbone. This directly tests the benefit of the depth-equivariant architecture.
2.  Investigating the type of normalization and pooling used with the SES blocks (3D vs 2D). The paper already did this, but it's a key implementation detail worth highlighting as an ablation.
3.  Comparing the SES convolution approach with the Log-Polar convolution approach as the basis for scale/depth equivariance.

The paper evaluates performance using AP$_{3D}$ and AP$_{BEV}$ on KITTI and Waymo, typically reported for different difficulty levels (Easy, Moderate, Hard for KITTI; Level 1, Level 2 for Waymo). Since the method focuses on depth, including depth estimation metrics (like Abs Rel, RMSE) is also relevant, as shown in the paper's ablation table (Table 3).

I will propose these three ablations, ranked by importance, using AP$_{3D}$ (Moderate) and AP$_{BEV}$ (Moderate) on KITTI as representative detection metrics, and Abs Rel and RMSE as representative depth metrics, consistent with the paper's Table 3.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Vanilla Backbone Comparison
- **Ablated Part**: DEVIANT's Scale Equivariant Steerable (SES) backbone
- **Action**: REPLACE
- **Replacement**: 
  - Vanilla CNN backbone (e.g., original DLA-34)
- **Metrics**: AP_3D (Moderate), AP_BEV (Moderate), Abs Rel, RMSE

### Batch Norm and Pooling Type
- **Ablated Part**: Using 3D Batch Norm and Pooling layers within the SES backbone
- **Action**: REPLACE
- **Replacement**: 
  - 2D Batch Norm and Pooling layers
- **Metrics**: AP_3D (Moderate), AP_BEV (Moderate), Abs Rel, RMSE

### Scale Equivariance Method Comparison
- **Ablated Part**: Using SES convolutions for scale/depth equivariance
- **Action**: REPLACE
- **Replacement**: 
  - Log-Polar convolutions
- **Metrics**: AP_3D (Moderate), AP_BEV (Moderate), Abs Rel, RMSE

</div>