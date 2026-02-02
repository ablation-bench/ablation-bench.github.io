<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Mitigating_Dataset_Bias_by_Using_Per_Sample_Gradient

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Mitigating Dataset Bias by Using Per-Sample Gradient" introduces a novel method called Per-sample Gradient-based Debiasing (PGD) to address dataset bias in machine learning models. The method involves three main steps: training a biased model, computing the importance of each sample based on the gradient norm, and training a debiased model using importance-batch sampling. The paper includes ablation studies on the generalized cross-entropy (GCE) loss and data augmentation, showing their impact on the method's performance.

The existing ablation studies focus on the importance of GCE and data augmentation, but there are other components of the PGD method that could be further explored. One such component is the choice of gradient norm used to compute the sampling probability. The paper briefly mentions different norms (L1, L2, L∞) but does not provide a detailed ablation study on their impact. Another potential area for ablation is the effect of using different sampling strategies in the importance-batch sampling step, as the current method uses a specific strategy based on the gradient norm.

To address these gaps, I propose two missing ablation studies. The first study investigates the impact of different gradient norms on the performance of PGD, as the choice of norm could significantly affect the identification of bias-conflicting samples. The second study explores alternative sampling strategies in the importance-batch sampling step, which could provide insights into the robustness and effectiveness of the current sampling method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study on Gradient Norms
- **Ablated Part**: Gradient norm used for computing sampling probability
- **Action**: REPLACE
- **Replacement**: 
  - L1
  - L2
  - L∞
- **Metrics**: unbiased test accuracy, average test accuracy

### Ablation Study on Sampling Strategies
- **Ablated Part**: Sampling strategy in importance-batch sampling
- **Action**: REPLACE
- **Replacement**: 
  - uniform sampling
  - stratified sampling
  - random sampling
- **Metrics**: unbiased test accuracy, average test accuracy

</div>