<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Improving_Adversarial_Robustness_by_Contrastive_Guided_Diffusion_Process

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes Contrastive-DP, which incorporates contrastive learning into diffusion models to improve adversarial robustness. The authors already conducted several ablation studies:

1. Different contrastive loss designs (InfoNCE vs HNM with/without embedding)
2. Sensitivity analysis of λ parameter (strength of contrastive loss)
3. Different data selection methods for synthetic data

However, there are two important aspects that lack proper ablation analysis:

1. The choice of feature extractor for contrastive learning is crucial but not thoroughly investigated. The authors use a pre-trained WRN-28-10 model but don't explore alternatives.

2. The temperature parameter τ in the contrastive loss functions is fixed (τ=0.1 for InfoNCE and τ=10 for HNM) without justification. This is a critical hyperparameter that controls the sharpness of the similarity distribution.

These components directly affect the method's core contribution - the contrastive guidance - and should be ablated to understand their impact.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Feature Extractor Ablation
- **Ablated Part**: Pre-trained model used as feature extractor for contrastive loss
- **Action**: REPLACE
- **Replacement**: 
  - ResNet-50
  - EfficientNet-B0
  - MobileNetV2
- **Metrics**: clean accuracy, robust accuracy

### Temperature Parameter Study
- **Ablated Part**: Temperature parameter τ in contrastive loss functions
- **Action**: REPLACE
- **Replacement**: 
  - 0.01
  - 0.05
  - 0.5
  - 1.0
- **Metrics**: clean accuracy, robust accuracy

</div>