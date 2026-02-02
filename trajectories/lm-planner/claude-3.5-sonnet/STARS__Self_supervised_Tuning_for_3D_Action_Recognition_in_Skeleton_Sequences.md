<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/STARS__Self_supervised_Tuning_for_3D_Action_Recognition_in_Skeleton_Sequences

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents STARS, a two-stage framework for self-supervised learning of skeleton-based action recognition that combines masked prediction (MAMP) with contrastive tuning (NNCLR).

The existing ablations in the paper cover:
1. Tuning strategy comparison (DINO vs MoCo vs NNCLR)
2. Effect of augmentations
3. Layer-wise learning rate decay
4. Queue size impact
5. Combining MAMP and NNCLR in second stage
6. Training NNCLR from scratch
7. Using naive MAE instead of MAMP

However, there are two important aspects that lack proper ablation analysis:

1. The masking ratio in the first stage (MAMP) is a critical hyperparameter that could significantly impact the learned representations. While the paper uses MAMP's default masking strategy, it doesn't explore how different masking ratios affect the final performance after contrastive tuning.

2. The paper uses layer-wise learning rate decay to tune only the second half of the encoder layers in stage 2, but doesn't justify this design choice through ablation. Testing different portions of encoder layers for tuning (e.g., last 25%, last 75%, all layers) could provide insights into the optimal tuning strategy.

These ablations would help understand key design choices and their impact on the method's effectiveness.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Masking Ratio Ablation
- **Ablated Part**: masking ratio in MAMP stage
- **Action**: REPLACE
- **Replacement**: 
  - 0.3
  - 0.5
  - 0.7
  - 0.9
- **Metrics**: KNN accuracy, Linear evaluation accuracy, Few-shot accuracy

### Encoder Tuning Depth
- **Ablated Part**: portion of encoder layers tuned in contrastive stage
- **Action**: REPLACE
- **Replacement**: 
  - last 25%
  - last 50%
  - last 75%
  - all layers
- **Metrics**: KNN accuracy, Linear evaluation accuracy, Few-shot accuracy

</div>