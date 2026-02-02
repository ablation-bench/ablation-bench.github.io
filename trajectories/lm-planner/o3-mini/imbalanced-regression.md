<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/imbalanced-regression

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Below are five carefully ranked ablation studies that target the key components of the DIR method. The first two ablations aim to show the individual contributions of the two core components, FDS and LDS, by removing them one at a time. This helps isolate their impact on performance using common regression metrics (such as MAE, RMSE, and Pearson correlation) that are also reported in the paper. The third ablation study investigates the choice of the symmetric kernel used in both label and feature smoothing, replacing the default (e.g., Gaussian) with alternatives like Laplacian or Uniform. The fourth ablation focuses on the momentum update used for estimating feature statistics in FDS by replacing it with different momentum settings (including effectively “no momentum”). Finally, the fifth ablation alters the target bin resolution used for grouping continuous labels in both LDS and FDS, which directly affects the smoothing operation. These ablations will provide insight into how much each element contributes to mitigating imbalanced regression and ensuring accurate extrapolation/interpolation across continuous targets.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation FDS Removal
- **Ablated Part**: Feature Distribution Smoothing (FDS) calibration layer and its statistic transfer (whitening and re-coloring) component
- **Action**: REMOVE
- **Metrics**: MAE, RMSE, PearsonCorrelation

### Ablation LDS Removal
- **Ablated Part**: Label Distribution Smoothing (LDS) component and its associated cost-sensitive re-weighting based on smoothed label density
- **Action**: REMOVE
- **Metrics**: MAE, RMSE, PearsonCorrelation

### Kernel Type Replacement
- **Ablated Part**: The symmetric kernel function used in both LDS and FDS for smoothing the label and feature distributions
- **Action**: REPLACE
- **Replacement**: 
  - Gaussian
  - Laplacian
  - Uniform
- **Metrics**: MAE, RMSE, PearsonCorrelation

### Momentum Update Ablation in FDS
- **Ablated Part**: Exponential moving average (momentum) used to update running feature statistics in FDS
- **Action**: REPLACE
- **Replacement**: 
  - 0
  - 0.5
  - 0.9
  - 0.95
- **Metrics**: MAE, RMSE, PearsonCorrelation

### Bin Resolution Ablation
- **Ablated Part**: The target grouping/bin size for partitioning the continuous label space for both LDS and FDS
- **Action**: REPLACE
- **Replacement**: 
  - 0.5
  - 1
  - 2
- **Metrics**: MAE, RMSE, PearsonCorrelation

</div>