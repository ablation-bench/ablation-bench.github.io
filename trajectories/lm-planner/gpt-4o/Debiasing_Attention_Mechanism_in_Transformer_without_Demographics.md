<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Debiasing_Attention_Mechanism_in_Transformer_without_Demographics

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Debiasing Attention Mechanism in Transformer without Demographics" introduces a novel approach to mitigate bias in transformers by modifying the attention mechanism without relying on sensitive demographic labels. The method involves two main components: normalizing and applying absolute value operations to queries and keys to reduce bias in attention weight allocation, and using contrastive learning for local alignment on values to further reduce bias. The paper also proposes a memory-efficient strategy by debiasing only the last encoder layer in pre-trained models.

The existing ablation studies in the paper focus on the importance of local alignment and debiasing attention weights. However, there are potential areas for further exploration. One missing ablation could be the impact of the normalization and absolute value operations on queries and keys separately. Another could be the effect of the number of value vectors selected for local alignment on the overall fairness and accuracy.

1. **Normalization and Absolute Value Operations**: The paper applies both normalization and absolute value operations to queries and keys. An ablation study could investigate the impact of each operation separately to understand their individual contributions to reducing bias.

2. **Number of Value Vectors for Local Alignment**: The paper selects the top two value vectors for local alignment. An ablation study could explore the effect of varying the number of value vectors (e.g., 1, 3, 4) on the model's fairness and accuracy.

These ablations would provide insights into the individual contributions of the components and the sensitivity of the method to hyperparameter choices, enhancing the understanding of the proposed debiasing strategy.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Normalization and Absolute Value Operations
- **Ablated Part**: Normalization and absolute value operations on queries and keys
- **Action**: REPLACE
- **Replacement**: 
  - Normalization only
  - Absolute value only
- **Metrics**: DP, EOp, EOd, ACC

### Ablation on Number of Value Vectors for Local Alignment
- **Ablated Part**: Number of value vectors selected for local alignment
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 3
  - 4
- **Metrics**: DP, EOp, EOd, ACC

</div>