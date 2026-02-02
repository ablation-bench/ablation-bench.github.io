<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/simcse

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Below are five targeted ablation studies ranked by their importance. The top experiments focus on the core contribution of SimCSE – the use of dropout as a minimal data augmentation mechanism in the unsupervised setting and its role in preserving alignment and uniformity. The first two ablations remove or fix the dropout randomness, directly examining its impact on representation quality (measured via STS-B Spearman’s correlation, alignment, and uniformity). The third ablation replaces dropout‐based noise with discrete textual augmentations (e.g. word deletion, cropping, synonym replacement) to test if the simplicity of dropout is indispensable. In the supervised setting, the fourth ablation removes the addition of hard negatives (i.e. contradiction examples) from the NLI dataset, a key factor elevating performance on STS tasks. Finally, the fifth ablation replaces the shared (single) encoder used in unsupervised SimCSE with a dual encoder to verify that sharing parameters is beneficial for stable alignment. These experiments together shed light on the major components influencing the performance of SimCSE.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Remove Dropout Noise
- **Ablated Part**: Dropout-based noise used to generate different embeddings for identical sentences in unsupervised SimCSE
- **Action**: REMOVE
- **Metrics**: STS-B Spearman's correlation, Alignment, Uniformity

### Ablation 2: Fixed Dropout Mask
- **Ablated Part**: Stochastic variation provided by independent dropout masks during positive pair generation
- **Action**: REPLACE
- **Replacement**: 
  - fixed (shared) dropout mask
- **Metrics**: STS-B Spearman's correlation, Alignment, Uniformity

### Ablation 3: Replace Dropout with Discrete Augmentation
- **Ablated Part**: The minimal data augmentation mechanism (dropout noise) used to perturb inputs in unsupervised SimCSE
- **Action**: REPLACE
- **Replacement**: 
  - word deletion
  - word cropping
  - synonym replacement
- **Metrics**: STS-B Spearman's correlation, Alignment, Uniformity

### Ablation 4: Remove Hard Negatives in Supervised SimCSE
- **Ablated Part**: Incorporation of contradiction pairs as hard negatives in the supervised contrastive objective
- **Action**: REMOVE
- **Metrics**: STS-B Spearman's correlation, Average STS Spearman's correlation

### Ablation 5: Use Dual Encoder Architecture
- **Ablated Part**: The use of a single shared encoder in unsupervised SimCSE for generating positive pairs
- **Action**: REPLACE
- **Replacement**: 
  - dual encoder (two independent encoders)
- **Metrics**: STS-B Spearman's correlation, Transfer task accuracy

</div>