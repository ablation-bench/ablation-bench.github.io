<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/upet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

In our ablation plan, we select the most central components of the UPET framework that contribute to both its robustness and efficiency. The first study targets the uncertainty estimation module, which uses Monte Carlo dropout to reliably sample pseudo-labeled examples. Removing this component (i.e. relying solely on confidence) allows us to assess its contribution to noise reduction. Next, we examine the Easy-Hard Contrastive Tuning mechanism, which uses hard examples as negatives to regularize the student model; removing it tests its effect on avoiding overfitting and preserving semantic discrimination. Then, we study the choice of loss by replacing the partially huberised cross-entropy (PHCE) loss with standard cross-entropy loss, thus evaluating the benefits of gradient clipping in handling noisy labels. In addition, we evaluate the influence of the parameter-efficient learning approach by replacing it with full fine-tuning, so as to understand the trade-offs between efficiency (i.e. trainable parameter count and training cost) and performance. Finally, given that UPET integrates multiple prediction paradigms (for instance, Head-Tuning versus Prompt-Tuning variants such as Ptuning, Prefix-tuning, or Adapter-tuning), we plan to compare these different parameter-efficient methods to analyze their effectiveness and efficiency.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Uncertainty Estimation
- **Ablated Part**: Monte Carlo dropout-based uncertainty estimation used for reliable example sampling in the RES module
- **Action**: REMOVE
- **Metrics**: Accuracy, F1 Score, Training Efficiency

### Ablation: Remove Easy-Hard Contrastive Tuning
- **Ablated Part**: Easy-Hard Contrastive Tuning regularization incorporated during student model training
- **Action**: REMOVE
- **Metrics**: Accuracy, Robustness, Generalization

### Ablation: Replace PHCE Loss
- **Ablated Part**: Adoption of partially huberised cross-entropy (PHCE) loss to mitigate noisy labels during training
- **Action**: REPLACE
- **Replacement**: 
  - Standard Cross-Entropy Loss
- **Metrics**: Accuracy, Convergence Rate, Robustness

### Ablation: Full Fine-Tuning Instead of Parameter-Efficient Tuning
- **Ablated Part**: Parameter-Efficient Learning (PEL) paradigms used for student training
- **Action**: REPLACE
- **Replacement**: 
  - Full Fine-tuning
- **Metrics**: Accuracy, Training Efficiency, Parameter Count

### Ablation: Evaluate Different PEL Methods
- **Ablated Part**: Different parameter-efficient tuning strategies (e.g., Head-Ptuning, Head-Prefix, Head-Adapter, Prompt-Ptuning, Prompt-Prefix, Prompt-Adapter)
- **Action**: REPLACE
- **Replacement**: 
  - Head-Ptuning
  - Head-Prefix
  - Head-Adapter
  - Prompt-Ptuning
  - Prompt-Prefix
  - Prompt-Adapter
- **Metrics**: Accuracy, Efficiency, Robustness

</div>