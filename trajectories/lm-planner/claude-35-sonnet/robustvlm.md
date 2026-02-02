<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/robustvlm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, the key components of the method are:

1. The unsupervised embedding loss (L_FARE) that aims to keep features of perturbed points close to unperturbed ones from original CLIP.

2. The use of PGD (Projected Gradient Descent) to solve the inner maximization problem.

3. The L2 norm used to measure distance between embeddings.

4. The epsilon parameter that controls the perturbation size in the L-infinity norm threat model.

The most important ablations should investigate:

1. The impact of the unsupervised loss vs supervised alternatives
2. The effect of different perturbation sizes (epsilon)
3. The choice of distance metric in the embedding space
4. The optimization method for solving the inner maximization

I'll rank these in order of importance based on their likely impact on the method's performance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Loss Function Ablation
- **Ablated Part**: Unsupervised embedding loss (L_FARE)
- **Action**: REPLACE
- **Replacement**: 
  - Supervised cross-entropy loss (TeCoA)
  - Contrastive loss
- **Metrics**: Zero-shot classification accuracy, CIDEr score, VQA accuracy, Robust accuracy under L-inf attacks

### Perturbation Size Study
- **Ablated Part**: Epsilon parameter in L-infinity constraint
- **Action**: REPLACE
- **Replacement**: 
  - 1/255
  - 2/255
  - 4/255
  - 8/255
- **Metrics**: Zero-shot classification accuracy, Robust accuracy under L-inf attacks, CIDEr score

### Distance Metric Ablation
- **Ablated Part**: L2 norm in embedding space
- **Action**: REPLACE
- **Replacement**: 
  - Cosine similarity
  - L1 norm
  - Huber loss
- **Metrics**: Zero-shot classification accuracy, CIDEr score, VQA accuracy, Robust accuracy under L-inf attacks

### Inner Maximization Method
- **Ablated Part**: PGD optimization
- **Action**: REPLACE
- **Replacement**: 
  - FGSM
  - MI-FGSM
  - AutoPGD
- **Metrics**: Zero-shot classification accuracy, Robust accuracy under L-inf attacks, Training time

</div>