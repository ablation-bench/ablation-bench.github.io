<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Learning_with_Instance_Dependent_Label_Noise__Balancing_Accuracy_and_Fairness

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Learning with Instance-Dependent Label Noise: Balancing Accuracy and Fairness" proposes a two-stage approach to learn from datasets with instance-dependent label noise. The approach utilizes anchor points, a small subset of data for which we know the ground truth labels, to learn the underlying pattern of label noise in pre-training. Then, it adds the remaining data for fine-tuning, minimizing a weighted cross-entropy loss based on the learned noise pattern.

The paper evaluates the proposed approach on five benchmark prediction tasks with two different label noise settings and demonstrates that it leads to consistent improvements over the state-of-the-art in discriminative performance (AUROC) while balancing model fairness (area under the equalized odds curve, AUEOC).

To further investigate the proposed approach, we suggest two missing ablation studies:

1. **Ablation Study 1: Effect of Anchor Points Selection Method**

In the original paper, the anchor points are selected randomly from the training data. However, it would be interesting to investigate the effect of different anchor points selection methods on the performance of the proposed approach. For example, we could select anchor points based on their uncertainty (e.g., using uncertainty sampling) or based on their representativeness (e.g., using clustering).

2. **Ablation Study 2: Effect of Weighting Scheme in Fine-Tuning**

In the fine-tuning stage, the proposed approach uses a weighted cross-entropy loss based on the learned noise pattern. However, it would be interesting to investigate the effect of different weighting schemes on the performance of the proposed approach. For example, we could use a uniform weighting scheme or a weighting scheme based on the instance-dependent label noise rates.

These ablation studies can provide further insights into the proposed approach and help to identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: anchor points selection method
- **Action**: REPLACE
- **Replacement**: 
  - random selection
  - uncertainty sampling
  - clustering
- **Metrics**: AUROC, AUEOC

### Ablation Study 2
- **Ablated Part**: weighting scheme in fine-tuning
- **Action**: REPLACE
- **Replacement**: 
  - uniform weighting
  - instance-dependent label noise rates
- **Metrics**: AUROC, AUEOC

</div>