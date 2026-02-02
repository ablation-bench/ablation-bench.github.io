<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/smoothnet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The first proposed ablation experiment focuses on the motion-aware branches. In SmoothNet, the authors explicitly inject velocity and acceleration information to help mitigate long-term jitters. Removing these branches would allow us to understand their impact on both the per‐frame precision (MPJPE) and smoothness (Accel). 

The second ablation changes the backbone used to extract temporal relations. Rather than relying on the fully-connected design chosen in SmoothNet, this study will replace the FCN with other common sequence models such as TCN and Transformers. This experiment can help validate that the chosen global receptive field (using FCN) indeed offers superior performance in capturing smooth motion information.

The third ablation investigates the effect of varying the sliding-window size. The method uses a sliding-window processing scheme to capture a long temporal receptive field. By testing different window sizes (e.g., 8, 16, and 32 frames), we can evaluate the trade-off between capturing sufficient motion history and potential over-smoothing.

Finally, the fourth ablation targets the residual connections in the fully-connected blocks. Since residual connections are crucial for stabilizing deep networks and ensuring effective gradient propagation, removing them enables us to assess their role in both reducing jitter and maintaining accurate pose estimations.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Motion-Aware Branch
- **Ablated Part**: Motion-aware branches that incorporate explicit velocity and acceleration cues in the network.
- **Action**: REMOVE
- **Metrics**: MPJPE, Accel

### Ablation: Alternative Temporal Modules
- **Ablated Part**: Temporal feature extraction module (currently a FCN) used for smoothing.
- **Action**: REPLACE
- **Replacement**: 
  - TCN
  - Transformer
- **Metrics**: MPJPE, Accel

### Ablation: Sliding Window Size
- **Ablated Part**: Sliding-window scheme that defines the temporal receptive field for refinement.
- **Action**: REPLACE
- **Replacement**: 
  - 8
  - 16
  - 32
- **Metrics**: MPJPE, Accel

### Ablation: Remove Residual Connections
- **Ablated Part**: Residual connections within the fully-connected blocks in the refinement network.
- **Action**: REMOVE
- **Metrics**: MPJPE, Accel

</div>