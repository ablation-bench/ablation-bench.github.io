<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Debiasing_Attention_Mechanism_in_Transformer_without_Demographics

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Let me analyze the paper's ablation studies and suggest important missing ablations. The paper already includes several ablation studies:

1. "w/o local alignment" - removing the local value alignment technique
2. "w/o debias attention" - removing both normalization and absolute values from q and k vectors
3. "w/o absolute value" - removing just the absolute value operation while keeping normalization

Looking at the method's key components, there are two important ablations missing:

1. The number of top attention weights (t) used for local alignment is fixed at t=2 in their experiments. This is a critical hyperparameter that determines how many value vectors are used for the contrastive learning, but its impact is not studied.

2. The paper proposes applying their debiasing technique only to the last encoder layer for efficiency, but doesn't validate if this is actually optimal compared to applying it to different/multiple layers. This is an important architectural choice that should be studied.

These ablations would help better understand the method's sensitivity to key design choices and validate the authors' decisions.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Top-t Ablation
- **Ablated Part**: number of top attention weights (t) used for local alignment
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 2
  - 4
  - 8
- **Metrics**: DP, EOp, EOd, ACC

### Layer Selection Ablation
- **Ablated Part**: which encoder layers to apply debiasing to
- **Action**: REPLACE
- **Replacement**: 
  - last layer only
  - first layer only
  - all layers
  - middle layer only
- **Metrics**: DP, EOp, EOd, ACC, GPU Memory (MiB)

</div>