<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Improving_the_Transferability_of_Adversarial_Attacks_through_Experienced_Precise_Nesterov_Momentum

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents two new components, Experienced Momentum (EM) and Precise Nesterov Momentum (PN), and already contains ablations comparing their individual contributions (by comparing ENI-FGSM, PNI-FGSM, and EPNI-FGSM) as well as studies on hyperparameters (µ and epochs). However, two critical factors have not been evaluated.

First, the EM component is trained on derived models obtained via Random Channels Swapping (RCS). While the paper motivates RCS as a means to prevent over-fitting, it does not study whether this specific derivation strategy is optimal. An ablation that removes RCS or replaces it with alternative augmentation techniques (e.g., random cropping, flipping, or no augmentation at all) would help assess whether the observed performance gains are uniquely attributable to RCS or whether other augmentation strategies provide similar benefits.

Second, the paper adopts a fixed step size (or learning rate) during the adversarial example crafting process. In the conclusion, the authors even point out that exploring the effect of a dynamic step size may further improve transferability. Thus, evaluating different learning rate scheduling strategies (such as cosine annealing, exponential decay, or cyclical learning rates) versus the fixed step could offer valuable insights into the importance of step size scheduling in maximizing attack transferability.

These two experiments would significantly contribute to understanding the contributions of the method components and could potentially lead to further enhancements.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Effect of Input Model Augmentation on EM Training
- **Ablated Part**: The derived model generation strategy using Random Channels Swapping (RCS) for training Experienced Momentum (EM)
- **Action**: REPLACE
- **Replacement**: 
  - No augmentation
  - Standard augmentations (e.g., random cropping, flipping)
  - RCS (default)
- **Metrics**: attack success rate on normally trained models, attack success rate on defense models

### Ablation: Dynamic Step Size Scheduling
- **Ablated Part**: The fixed step size used during adversarial example crafting with EPN-based attacks
- **Action**: REPLACE
- **Replacement**: 
  - Cosine annealing
  - Exponential decay
  - Cyclical learning rate
  - Fixed step (default)
- **Metrics**: attack success rate on normally trained models, attack success rate on defense models

</div>