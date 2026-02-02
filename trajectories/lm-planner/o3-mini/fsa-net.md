<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/fsa-net

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose four ablation studies to analyze the contribution of the key components in FSA-Net. The most critical part of the network is the fine-grained structure mapping module, whose role is to spatially group pixel-level features before aggregation. Removing it will show how much the spatial grouping contributes to pose accuracy. The second ablation focuses on the scoring function that computes the attention maps; by replacing the learnable 1×1 convolution with alternatives (variance-based or uniform scoring), we can assess the impact of different importance measures on the representative feature extraction. Third, we propose to remove one of the two parallel streams (i.e., using a single-stream architecture) to evaluate the benefit of having complementary feature extraction pathways with ReLU and Tanh activations. Finally, we examine the design of the mapping module by replacing its separable structure (where a shared linear map C is combined with stage-specific maps Mₖ) with a full non-separable mapping, to understand the trade-offs between parameter efficiency and performance. In all studies we will report head pose estimation error measured by the mean absolute error (MAE) for yaw, pitch, and roll.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Fine-Grained Structure Mapping
- **Ablated Part**: fine-grained structure mapping module for spatial grouping of pixel-level features
- **Action**: REMOVE
- **Metrics**: MAE_yaw, MAE_pitch, MAE_roll

### Ablation Scoring Function Variants
- **Ablated Part**: scoring function used to compute the attention maps
- **Action**: REPLACE
- **Replacement**: 
  - 1x1 convolution (learnable)
  - Variance-based scoring
  - Uniform scoring
- **Metrics**: MAE_yaw, MAE_pitch, MAE_roll

### Ablation Single-Stream Architecture
- **Ablated Part**: two-stream feature extraction architecture
- **Action**: REMOVE
- **Metrics**: MAE_yaw, MAE_pitch, MAE_roll

### Ablation Mapping Module Design
- **Ablated Part**: separable structure mapping (shared map C with stage-specific Mₖ)
- **Action**: REPLACE
- **Replacement**: 
  - Full non-separable mapping
- **Metrics**: MAE_yaw, MAE_pitch, MAE_roll

</div>