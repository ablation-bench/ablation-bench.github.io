<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/seg-uncertainty

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, the main contributions are:
1. The memory regularization in vivo approach that uses the model's own predictions to reduce inconsistency
2. A two-stage training process with different loss components

The key components that deserve ablation studies are:

1. The memory regularization loss (L_mr) which is central to the method
2. The two-classifier architecture (primary and auxiliary)
3. The two-stage training process
4. The combination of predictions from both classifiers during inference
5. The pseudo-label generation approach

I'll suggest ablations focusing on these key aspects, ranked by importance:

1. Memory regularization ablation - This is the core contribution
2. Classifier architecture ablation - To validate the two-classifier approach
3. Prediction combination ablation - To verify the inference strategy
4. Training stages ablation - To validate the two-stage approach
5. Pseudo-label generation ablation - To test different label generation strategies
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Memory Regularization Ablation
- **Ablated Part**: Memory regularization loss (L_mr)
- **Action**: REMOVE
- **Metrics**: mIoU, per-class IoU

### Classifier Architecture Study
- **Ablated Part**: Auxiliary classifier
- **Action**: REMOVE
- **Metrics**: mIoU, per-class IoU

### Prediction Combination Study
- **Ablated Part**: Inference prediction combination strategy
- **Action**: REPLACE
- **Replacement**: 
  - primary_only
  - auxiliary_only
  - weighted_average
- **Metrics**: mIoU, per-class IoU

### Training Stage Analysis
- **Ablated Part**: Two-stage training process
- **Action**: REPLACE
- **Replacement**: 
  - single_stage
  - three_stage
- **Metrics**: mIoU, per-class IoU

### Pseudo-Label Generation Study
- **Ablated Part**: Pseudo-label generation method
- **Action**: REPLACE
- **Replacement**: 
  - primary_only
  - auxiliary_only
  - confidence_thresholding
- **Metrics**: mIoU, per-class IoU, pseudo-label accuracy

</div>