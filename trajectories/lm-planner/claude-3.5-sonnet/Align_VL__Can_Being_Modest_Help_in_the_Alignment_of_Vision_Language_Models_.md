<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Align_VL__Can_Being_Modest_Help_in_the_Alignment_of_Vision_Language_Models_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents Align-VL, a method for multimodal alignment that uses two key components:
1. Random Perturbation (RP) - Adds Gaussian noise to simulate uncertainty
2. Embedding Smoothing (ES) - Smooths output distributions to reduce overconfidence

Looking at the existing ablations in Table 3 and Table 4, the authors have already studied:
- Individual effects of RP and ES
- Different types of ES (dynamic vs default α)

However, there are two important aspects that lack proper ablation studies:

1. The Gaussian noise level σ in Random Perturbation is fixed at 0.01 without justification. This is a critical hyperparameter that directly affects how much uncertainty is injected into the embeddings.

2. The paper uses DINOv2 ViT-G/14 and BGE-large as frozen encoders but doesn't explore how the choice of pre-trained encoders impacts performance. This is important since the method relies heavily on these frozen representations.

The metrics used in the paper are primarily R@1, R@5, and R@10 for both text-to-image and image-to-text retrieval tasks.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Noise Level Ablation
- **Ablated Part**: Gaussian noise level σ in Random Perturbation
- **Action**: REPLACE
- **Replacement**: 
  - 0.001
  - 0.01
  - 0.05
  - 0.1
- **Metrics**: text->image R@1, text->image R@5, text->image R@10, image->text R@1, image->text R@5, image->text R@10

### Encoder Architecture Ablation
- **Ablated Part**: Pre-trained visual and text encoders
- **Action**: REPLACE
- **Replacement**: 
  - CLIP ViT-L/14 + BERT-large
  - ViT-L/16 + RoBERTa-large
  - ConvNeXt-XL + DeBERTa-large
- **Metrics**: text->image R@1, text->image R@5, text->image R@10, image->text R@1, image->text R@5, image->text R@10

</div>