<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/rrl

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies focusing on the key innovations of RRL. First, Gradient Grafting is central to bridging the gap between the continuous and discrete representations. Replacing it with standard alternative optimization methods (e.g., the Straight-Through Estimator or ProxQuant) will help us assess its contribution to convergence and overall accuracy. Second, the improved logical activation functions were introduced to alleviate vanishing gradients; by replacing them with the original product‐based (non-projected) functions, we can evaluate their effect on training stability and rule complexity. Third, the end-to-end binarization layer that dynamically discretizes continuous features is essential for seamless integration. Replacing it with a fixed threshold or pre-binarized features will reveal its role in both predictive performance and interpretability. Fourth, the skip connections in the logical layers provide the flexibility to learn multi-level rules and adjust model depth. Removing these connections will help determine how much they contribute to performance versus rule simplicity. Finally, since RRL’s depth (i.e., the number of logical layers) impacts both accuracy and interpretability, we also propose to vary model depth by replacing the existing configuration with several options (e.g., 1–4 layers) to analyze this trade-off. These ablations together should highlight the relative importance of RRL’s major components.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Gradient Grafting
- **Ablated Part**: Gradient Grafting training mechanism that combines discrete and continuous gradient flows for parameter updates
- **Action**: REPLACE
- **Replacement**: 
  - Straight-Through Estimator (STE)
  - ProxQuant
- **Metrics**: F1 score, training convergence, accuracy on large datasets

### Ablation Logical Activation Functions
- **Ablated Part**: Improved logical activation functions designed to mitigate vanishing gradients
- **Action**: REPLACE
- **Replacement**: 
  - Original product-based logical functions without projection
- **Metrics**: F1 score, training convergence, rule complexity

### Ablation Binarization Layer
- **Ablated Part**: End-to-end binarization layer that discretizes continuous features dynamically
- **Action**: REPLACE
- **Replacement**: 
  - Fixed threshold-based discretization
  - Pre-binarized features
- **Metrics**: F1 score, model interpretability, rule complexity

### Ablation Skip Connections
- **Ablated Part**: Skip connections between logical layers that allow dynamic adjustment of model depth
- **Action**: REMOVE
- **Metrics**: F1 score, rule complexity, performance vs depth

### Ablation Model Depth
- **Ablated Part**: The number of logical layers in the RRL affecting both accuracy and interpretability
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 2
  - 3
  - 4
- **Metrics**: F1 score, model complexity, training time

</div>