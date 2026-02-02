<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/neuralpull

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The proposed ablation studies aim to individually assess the contribution of the core components in Neural-Pull. The first and most critical ablation targets the gradient-based pulling mechanism. By removing the simultaneous update of the predicted signed distance and its gradient, we can observe how essential the learned gradient direction is for accurately pulling query points onto the surface. The second study replaces the adaptive pulling stride (where the stride is given by the predicted signed distance) with a fixed stride value, testing if the adaptiveness contributes to better precision in surface reconstruction. The third experiment modifies the strategy for sampling query locations: rather than using an adaptive Gaussian (with variance set according to local point density), we test fixed variance values. This will help evaluate how sensitive the network is to the geometry of query sampling around the points. The fourth ablation examines the strategy used to select query locations per batch—comparing random selection from the full query set versus uniform selection based on the ground truth point cloud—to see how batch composition affects convergence and quality. Finally, the fifth study investigates the initialization strategy. Since the network is originally initialized with geometric network initialization (approximating a sphere’s SDF), replacing it with common alternatives (e.g. random or Xavier initialization) can quantify the importance of a proper prior to the learning dynamics and final reconstruction quality.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Gradient-based Pulling
- **Ablated Part**: Simultaneous update of signed distance and gradient in the pulling operation
- **Action**: REMOVE
- **Metrics**: ChamferDistance, NormalConsistency, F-score

### Ablation: Fixed Pulling Stride
- **Ablated Part**: Adaptive pulling stride computed from the predicted signed distance
- **Action**: REPLACE
- **Replacement**: 
  - 0.1
  - 0.5
  - 1.0
- **Metrics**: ChamferDistance, NormalConsistency, F-score

### Ablation: Query Sampling Distribution
- **Ablated Part**: Query location sampling strategy around surface points using an adaptive Gaussian variance
- **Action**: REPLACE
- **Replacement**: 
  - 0.001
  - 0.01
  - 0.1
- **Metrics**: ChamferDistance, NormalConsistency, F-score

### Ablation: Batch Query Selection Strategy
- **Ablated Part**: Method for composing each training batch of query locations (random selection vs. uniform sampling based on ground truth points)
- **Action**: REPLACE
- **Replacement**: 
  - random
  - uniform
- **Metrics**: ChamferDistance, NormalConsistency, F-score

### Ablation: Network Initialization Strategy
- **Ablated Part**: Initial network parameter setting (geometric initialization versus alternatives)
- **Action**: REPLACE
- **Replacement**: 
  - geometric
  - random
  - xavier
- **Metrics**: ChamferDistance, NormalConsistency, F-score

</div>