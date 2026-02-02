<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Quantifying_and_Enhancing_Multi_modal_Robustness_with_Modality_Preference

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Quantifying and Enhancing Multi-modal Robustness with Modality Preference" presents a theoretical analysis of the essential components influencing multi-modal robustness and introduces a training procedure called Certifiable Robust Multi-modal Training (CRMT) to improve robustness in a certifiable manner. The authors identify two essential components for achieving higher robustness: larger uni-modal representation margins and more reliable integration for modalities. They also reveal how the widespread issue of modality preference limits the multi-modal robustness by influencing the essential components and could lead to attacks on the specific modality being highly effective.

To further investigate the robustness of the proposed method, we suggest two missing ablation studies:

1. **Ablation of the orthogonal-based framework**: The authors mention that the orthogonal-based framework does not contribute to improved robustness. However, it would be interesting to see the results of an ablation study that removes the orthogonal-based framework from the CRMT procedure to understand its impact on the overall performance.
2. **Ablation of the margin regularization term**: The authors introduce a margin regularization term (Equation 12) to refine the maximum using the LogSumExp function. An ablation study that removes this term or replaces it with a different regularization technique would help understand its importance in the CRMT procedure.

These ablation studies would provide further insights into the effectiveness of the CRMT procedure and its components, allowing for a more comprehensive understanding of the proposed method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Orthogonal-Based Framework
- **Ablated Part**: orthogonal-based framework
- **Action**: REMOVE
- **Metrics**: clean accuracy, FGM attack accuracy, ℓ2-PGD attack accuracy

### Ablation of Margin Regularization Term
- **Ablated Part**: margin regularization term
- **Action**: REMOVE
- **Metrics**: clean accuracy, FGM attack accuracy, ℓ2-PGD attack accuracy

</div>