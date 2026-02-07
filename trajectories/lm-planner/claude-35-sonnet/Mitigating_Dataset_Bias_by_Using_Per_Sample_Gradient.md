<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Mitigating_Dataset_Bias_by_Using_Per_Sample_Gradient

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes PGD, a three-step method for debiasing:
1. Training a biased model with uniform batch sampling
2. Computing importance scores based on gradient norms
3. Training the debiased model using importance-based sampling

Looking at the existing ablations in the paper:
- They ablate the GCE parameter α
- They compare resampling vs reweighting
- They analyze different gradient norms (L1, L2, L∞)
- They test data augmentation impact

However, there are some important aspects that are not ablated:

1. The choice of using only the final FC layer gradients vs full model gradients. This is a key design choice that significantly impacts computational efficiency but its effect on performance is not studied.

2. The impact of the biased model architecture and training. The paper uses the same architecture for both biased and debiased models, but doesn't explore if a simpler/different architecture for the biased model could work better since it's only used for gradient computation.

I'll suggest these two as the most important missing ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Full vs FC-only Gradients
- **Ablated Part**: gradient computation scope
- **Action**: REPLACE
- **Replacement**: 
  - full model gradients
  - final FC layer gradients only
- **Metrics**: unbiased test accuracy, training time, memory usage

### Biased Model Architecture
- **Ablated Part**: biased model architecture
- **Action**: REPLACE
- **Replacement**: 
  - same as debiased model
  - half width model
  - quarter width model
- **Metrics**: unbiased test accuracy, gradient computation time

</div>