<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Quantifying_and_Enhancing_Multi_modal_Robustness_with_Modality_Preference

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Quantifying and Enhancing Multi-modal Robustness with Modality Preference" proposes a novel training procedure called Certifiable Robust Multi-modal Training (CRMT) to improve multi-modal robustness. The method is based on a theoretical analysis that identifies uni-modal margins and modality integration as key factors, and modality preference as a limitation. CRMT uses an orthogonal-based framework and a two-step training procedure. Step 1 aims to enlarge uni-modal margins using a specific regularization term (L1, Equation 12). Step 2 aims to adjust modality integration by explicitly optimizing modality-specific weights `a^(m)` based on a derived certified lower bound (L2, Equation 10).

The paper includes an ablation study in Figure 5, comparing Joint Training (JT), the orthogonal framework alone (OJT), CRMT with only Step 1 (CRMT-step-1), CRMT with only Step 2 (CRMT-step-2), and the full CRMT-JT. This ablation demonstrates that both steps contribute to robustness and the full method is superior.

However, the existing ablation does not fully disentangle the contributions of specific components within the CRMT steps. Based on the method description, two important missing ablations are identified:

1.  **The specific optimization strategy for modality-specific weights `a^(m)`:** The paper highlights the importance of adjusting modality integration and proposes optimizing the weights `a^(m)` in Step 2 based on the certified bound (L2). The existing ablation shows that CRMT-step-2 (which includes this optimization) is beneficial. However, it doesn't show whether this *specific* optimization strategy is necessary, or if the weights `a^(m)` could be learned implicitly during the standard training process (e.g., alongside the encoders and orthogonal classifiers in Step 1). Ablating the explicit L2 optimization of `a^(m)` would clarify the contribution of this core part of Step 2.

2.  **The specific formulation of the margin regularization term (L1):** Step 1 uses a particular LogSumExp formulation (Equation 12) to regularize uni-modal margins. While the ablation shows CRMT-step-1 (which includes this regularization) is effective, it doesn't demonstrate if this specific formulation is crucial. Replacing it with a more standard margin loss (like a hinge loss) would help determine if the proposed L1 term provides unique benefits.

These two ablations are crucial for understanding which specific technical contributions within CRMT are driving the performance improvements. Ablating the explicit optimization of `a^(m)` (Ablation 1) is arguably more central to the paper's core idea of using the certified bound to guide integration, making it slightly more important than Ablation 2.

The metrics used in the paper's experimental section (Tables 1 and 2) include clean accuracy, adversarial accuracy under multi-modal attacks (FGM, ℓ2-PGD), and adversarial accuracy under uni-modal attacks (FGM #v, FGM #a, ℓ2-PGD #v, ℓ2-PGD #a), and missing modality accuracy. The most comprehensive set of robustness metrics is presented in Table 2.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Explicit Modality Weight Optimization
- **Ablated Part**: Explicit optimization of modality-specific weights a^(m) using the certified bound (L2 loss in Step 2 of CRMT)
- **Action**: REMOVE
- **Metrics**: Clean accuracy, FGM multi-modal accuracy, ℓ2-PGD multi-modal accuracy, FGM #v accuracy, FGM #a accuracy, ℓ2-PGD #v accuracy, ℓ2-PGD #a accuracy, Missing modality #v accuracy, Missing modality #a accuracy

### Ablation of L1 Regularization Formulation
- **Ablated Part**: The specific LogSumExp margin regularization term L1 (Equation 12) in Step 1 of CRMT
- **Action**: REPLACE
- **Replacement**: 
  - Standard margin loss (e.g., hinge loss) on uni-modal scores
- **Metrics**: Clean accuracy, FGM multi-modal accuracy, ℓ2-PGD multi-modal accuracy, FGM #v accuracy, FGM #a accuracy, ℓ2-PGD #v accuracy, ℓ2-PGD #a accuracy, Missing modality #v accuracy, Missing modality #a accuracy

</div>