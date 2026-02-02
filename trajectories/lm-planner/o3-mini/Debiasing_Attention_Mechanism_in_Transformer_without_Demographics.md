<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Debiasing_Attention_Mechanism_in_Transformer_without_Demographics

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The current paper presents ablations that remove key components of the method (local alignment and debiasing via absolute value operations on normalized queries and keys) to demonstrate their individual contributions. However, two important aspects remain unexplored. First, although the paper advocates for debiasing only the last encoder to maintain memory efficiency, it remains unclear how the placement of the debiasing module (e.g., applying it to all encoder layers versus only the last or an intermediate layer) affects fairness‐accuracy trade-offs and energy consumption. Investigating different positions can reveal whether spreading the debiasing operation throughout the network can further mitigate bias or if the last-layer deployment is optimal. Second, the debias mechanism relies on a specific normalization approach (using running mean and standard deviation as in BatchNorm) before applying the absolute value. Exploring alternative normalization strategies—such as Layer Normalization (which is commonly used in transformers) or standard BatchNorm—may determine if performance and fairness improvements are sensitive to the normalization technique. These ablations would provide deeper insights into the design choices made in the method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Layer-wise Debiasing
- **Ablated Part**: The location of the debiasing module within the transformer encoder layers
- **Action**: REPLACE
- **Replacement**: 
  - last encoder only
  - all encoder layers
  - selected intermediate encoder
- **Metrics**: DP, EOp, EOd, ACC, E(Wh)

### Normalization Strategy Ablation
- **Ablated Part**: The normalization method applied to queries and keys before taking the absolute value
- **Action**: REPLACE
- **Replacement**: 
  - running mean/std (current)
  - LayerNorm
  - BatchNorm
- **Metrics**: DP, EOp, EOd, ACC

</div>