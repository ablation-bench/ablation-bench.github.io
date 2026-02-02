<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Certified_Robustness_on_Visual_Graph_Matching_via_Searching_Optimal_Smoothing_Range

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The first ablation study we propose is to quantify the impact of the optimal smoothing range search – a core contribution of the paper. Currently, CR-OSRS uses a global optimization algorithm to search for the optimal joint Gaussian parameters (σ and correlation parameter b) that balance certified robustness with matching performance. In this missing ablation, we suggest replacing the global optimization with fixed joint Gaussian parameters (i.e., using manually chosen constant values for σ and b). This experiment will reveal how much the optimal smoothing range search contributes to improving certified accuracy (CA), average certified radius (ACR), and the detailed marginal radii (∥δ∥lower, ∥δ∥upper, ∥δ∥volume).

The second ablation study addresses the pixel perturbation scenario. In practice, the paper chooses to use an isotropic Gaussian distribution for image pixel perturbations due to the computational complexity of modeling correlations among pixels. However, it is conceivable that a joint (e.g., block‐based or structure-aware) Gaussian smoothing approach that captures spatial correlations among image pixels might improve robustness certification. Comparing such a scheme against the standard isotropic noise will help understand whether structural correlations in pixel space can further boost certified robustness under adversarial pixel perturbations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Optimal Smoothing Range Search
- **Ablated Part**: Global optimization of joint Gaussian noise parameters (σ and correlation parameter b) used for optimal smoothing range search
- **Action**: REPLACE
- **Replacement**: 
  - fixed joint Gaussian with constant σ and b=0.5
  - fixed joint Gaussian with constant σ and b=0.2
- **Metrics**: CA, ACR, ∥δ∥lower, ∥δ∥upper, ∥δ∥volume

### Ablation Joint Gaussian for Pixel Perturbations
- **Ablated Part**: Isotropic Gaussian smoothing used for image pixel perturbations
- **Action**: REPLACE
- **Replacement**: 
  - block-based joint Gaussian smoothing (e.g., using 4x4 or 8x8 pixel blocks)
  - structure-aware joint Gaussian smoothing for pixels
- **Metrics**: CA, ACR, ∥δ∥lower, ∥δ∥upper, ∥δ∥volume

</div>