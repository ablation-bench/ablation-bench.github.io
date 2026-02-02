<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Masked_Image_Modeling_with_Denoising_Contrast

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Masked Image Modeling with Denoising Contrast" introduces ConMIM, a self-supervised pre-training method for Vision Transformers that combines masked image modeling with a denoising contrastive objective. The core components are the patch-level dynamic dictionary, the denoising contrastive loss (an InfoNCE loss applied to masked patch predictions), and two asymmetric designs: asymmetric image perturbations and asymmetric model progress rates (using a momentum encoder).

The paper includes several ablation studies in Section 5.4 and Appendix B:
1.  **Denoising Auto-Encoding Mechanism:** Shows the importance of patch-level supervision and masking (Table 6).
2.  **Patch-Level Dynamic Dictionary:** Explores dictionary size (intra-image vs. intra-GPU negatives) and filtering noisy negatives (Table 7).
3.  **Asymmetric Designs:** Ablates asymmetric image perturbations (using symmetric strong or basic aug, or switching them) and asymmetric model progress rates (removing the momentum encoder) individually (Table 8).
4.  **Hyper-parameters:** Analyzes masking ratio, temperature, and momentum coefficient (Tables 15, 16, 17).
5.  **Key Components Analysis (Appendix B.5):** Discusses the relative importance and interactions of the three main components (denoising contrastive loss, asymmetric image perturbations, asymmetric model progress rates). It states the importance ranking is denoising contrastive loss > asymmetric model progress rates > asymmetric image perturbations. It also discusses what happens when changing the loss or removing one asymmetric part.

Based on this analysis, I identify two important missing ablation studies:

1.  **Ablation of the Stop-Gradient Operation:** The denoising contrastive loss (Eq. 3) uses a stop-gradient operation (`sg[f(x)_i]`) on the keys derived from the full input image. This is a standard technique in contrastive learning (like MoCo) to prevent representational collapse where the model learns trivial solutions. The paper mentions this is done to avoid "information leakage and useless denoising" and only backpropagate gradients through the corrupted input path. However, there is no experiment directly ablating this stop-gradient operation to show its necessity and impact on performance or training stability. This is a fundamental design choice for the contrastive loss component.

2.  **Ablation of Combined Asymmetric Designs:** The paper ablates the two asymmetric designs (image perturbations and model progress rates) individually in Table 8. It shows that removing asymmetric model progress rates has a significant negative impact (-1.98%), while removing asymmetric image perturbations has a smaller impact (-0.10% or -0.16%). The full ConMIM model uses *both* asymmetric designs. While Appendix B.5 discusses their relative importance, there is no quantitative ablation showing the combined effect of removing *both* asymmetric designs simultaneously (i.e., using symmetric augmentation for both inputs AND using the same in-training encoder for both). This experiment would quantify the total performance gain attributable to the combination of these two asymmetric components over a baseline that uses denoising contrast but with symmetric inputs and models.

Ranking these two, the stop-gradient ablation is slightly more critical as it tests a mechanism essential for the stability of the contrastive loss itself. Removing it could potentially lead to training failure or severe performance degradation, highlighting its fundamental role. The combined asymmetric designs ablation is also important as it quantifies the total contribution of the enhancements, but the individual contributions are already shown.

Therefore, the most important missing ablations are the stop-gradient operation and the combined effect of the asymmetric designs. The primary metric used for ablations in the paper is ImageNet Top-1 accuracy after fine-tuning.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Stop-Gradient
- **Ablated Part**: Stop-gradient operation on the keys (full input features) in the denoising contrastive loss.
- **Action**: REMOVE
- **Metrics**: ImageNet Acc.

### Ablation of Combined Asymmetric Designs
- **Ablated Part**: Both asymmetric image perturbations and asymmetric model progress rates.
- **Action**: REPLACE
- **Replacement**: 
  - Symmetric image perturbations (e.g., basic augmentation for both full and corrupted inputs) and symmetric model progress rates (using the in-training encoder for both full and corrupted inputs).
- **Metrics**: ImageNet Acc.

</div>