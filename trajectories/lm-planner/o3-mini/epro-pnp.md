<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/epro-pnp

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Here we propose five key ablation studies aimed at dissecting the contributions of the core components of EPro‐PnP. The first ablation compares the full probabilistic formulation (with its KL divergence loss that models pose ambiguity) against a deterministic alternative (e.g. implicit differentiation with standard reprojection loss) to validate the benefits of outputting a pose distribution. The second study removes the derivative regularization loss, which is designed to steer the gradient (via a Gauss–Newton step) and disentangle the 2D–3D correspondences, so as to measure its impact on training stability and final pose accuracy. The third experiment focuses on the Monte Carlo Pose Loss by varying the parameters of the Adaptive Multiple Importance Sampling (AMIS) algorithm (such as iteration count and sample size) to judge how sensitive the integration approximation is, both in terms of accuracy (using pose metrics such as ADD(-S) and reprojection error) and runtime. Fourth, we examine the influence of the robust loss function by replacing the adaptive Huber kernel with alternatives (a fixed-threshold Huber kernel and plain L2 loss) to see if the robustness against outliers affects performance. Finally, the last ablation removes the dynamic KL loss weighting mechanism (which normalizes gradient magnitudes through an exponential moving average of the sum of weights) to determine its role in ensuring stable convergence. Together, these ablations will shed light on which components most critically contribute to handling pose ambiguity and achieving state-of-the-art monocular 6DoF object pose estimation.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Deterministic vs Probabilistic PnP
- **Ablated Part**: Probabilistic pose distribution and KL divergence loss that models pose ambiguity in EPro-PnP
- **Action**: REPLACE
- **Replacement**: 
  - Deterministic PnP using implicit differentiation
  - Standard reprojection loss without probabilistic modeling
- **Metrics**: ADD(-S), Reprojection Error, Pose Estimation Accuracy

### Remove Derivative Regularization Loss
- **Ablated Part**: Derivative regularization loss that refines local pose estimates and disentangles 2D-3D correspondences
- **Action**: REMOVE
- **Metrics**: ADD(-S), Reprojection Error, Training Convergence/Stability

### Vary Monte Carlo Pose Loss Parameters
- **Ablated Part**: Adaptive Multiple Importance Sampling (AMIS) settings in the Monte Carlo integration for approximating the normalization term in the KL loss
- **Action**: REPLACE
- **Replacement**: 
  - AMIS iteration count T: [1, 4, 8]
  - Samples per iteration K': [32, 64, 128]
- **Metrics**: ADD(-S), Reprojection Error, Inference Time

### Robust Loss Function Variation
- **Ablated Part**: Adaptive Huber kernel used to robustify the weighted reprojection errors
- **Action**: REPLACE
- **Replacement**: 
  - Fixed-threshold Huber kernel
  - Plain L2 loss
- **Metrics**: ADD(-S), Reprojection Error

### Remove Dynamic KL Loss Weighting
- **Ablated Part**: Dynamic KL loss weighting mechanism that normalizes the effect of the 2D weight magnitudes using an EMA
- **Action**: REMOVE
- **Metrics**: ADD(-S), Reprojection Error, Training Stability

</div>