<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/seg-uncertainty

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies focusing on the core contribution—the memory regularization—and its interactions with other components in the overall scene adaptation framework. The first experiment removes the memory regularization entirely to quantify its overall contribution compared to the baseline without it. Next, we isolate the effect of memory regularization during Stage-II (self‐training with pseudo labels) by removing the regularization in that stage only, as its smoothing effect is claimed to mitigate noise from pseudo labels. We then study the design choice of using the network’s own memory (in vivo) by replacing it with an external memory module (e.g., Mean Teacher or Mutual Learning) to validate that using in-network memories is beneficial. Furthermore, we plan to conduct a sensitivity analysis by varying the weight (lambda) of the memory regularization loss to assess stability and performance sensitivity. Finally, we investigate the specific formulation of the memory loss by comparing the symmetric (bidirectional) KL divergence versus a unidirectional formulation to evaluate if enforcing full consistency is required. These experiments are ranked in order of importance based on their potential impact on verifying the claimed benefits of the memory regularization.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Memory Regularization Removal
- **Ablated Part**: Memory regularization loss that enforces consistency between the primary and auxiliary classifiers on the target domain (both Stage-I and Stage-II)
- **Action**: REMOVE
- **Metrics**: mIoU

### Stage-II Memory Regularization Ablation
- **Ablated Part**: Memory regularization applied during the self-training stage with pseudo labels
- **Action**: REMOVE
- **Metrics**: mIoU

### External Memory Module Replacement
- **Ablated Part**: In vivo memory regularization mechanism using the network’s internal consistency
- **Action**: REPLACE
- **Replacement**: 
  - Mean Teacher
  - Mutual Learning
- **Metrics**: mIoU

### Memory Regularization Weight Sensitivity
- **Ablated Part**: The weight (lambda) assigned to the memory regularization loss
- **Action**: REPLACE
- **Replacement**: 
  - 0
  - 0.05
  - 0.1
  - 0.2
- **Metrics**: mIoU

### Directional Consistency Loss
- **Ablated Part**: The symmetric (bidirectional) KL divergence used to enforce consistency between classifiers
- **Action**: REPLACE
- **Replacement**: 
  - Bidirectional KL
  - Unidirectional KL (primary guided by auxiliary)
- **Metrics**: mIoU

</div>