<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/upet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Uncertainty-aware Parameter-Efficient Self-training for Semi-supervised Language Understanding (UPET)" proposes a novel framework combining self-training with uncertainty estimation and parameter-efficient learning. The core contributions are the Reliable Example Sampling (RES) mechanism, which uses confidence and MC dropout-based uncertainty to select pseudo-labeled data, and the Efficient Robust Tuning (ERT) for the student model, which incorporates Parameter-Efficient Learning (PEL), Partially Huberised Cross-Entropy (PHCE) loss, and Easy-Hard Contrastive Tuning.

To understand the contribution of each of these components, a series of ablation studies is necessary. The most important ablations should target the key novelties introduced by UPET.

1.  **Reliable Example Sampling (RES):** The paper claims that judiciously selecting reliable examples mitigates noise. Ablating the entire RES mechanism and comparing it to simpler sampling strategies (like just using confidence or even random sampling) will show the overall effectiveness of the proposed sampling approach. This is a high-priority ablation as it tests a core part of the "Uncertainty-aware" aspect.
2.  **Uncertainty Estimation:** Within RES, the use of MC dropout for uncertainty estimation is a specific technical contribution. Ablating *only* the uncertainty part while still using confidence for sampling will isolate the benefit of adding uncertainty to the selection process. This is a more fine-grained ablation of RES.
3.  **Easy-Hard Contrastive Tuning:** This is presented as a novel regularization technique to improve robustness during student training. Removing this component will demonstrate its impact on the student model's performance and robustness, especially in the presence of potential residual noise in the selected data.
4.  **Parameter-Efficient Learning (PEL):** While the paper explores different PEL methods, a fundamental question is how UPET performs *without* PEL, i.e., using standard full fine-tuning for the student. This ablation directly tests the "Parameter-Efficient" claim and helps understand the trade-off between efficiency and performance compared to a non-PEL self-training baseline. This is crucial for validating the efficiency aspect of UPET.
5.  **Partially Huberised Cross-Entropy (PHCE) Loss:** The PHCE loss is used for robustness against noisy labels during student training. Replacing it with a standard Cross-Entropy loss will show the specific contribution of this loss function in handling noise compared to a more conventional approach.

These five ablations cover the main novel components of the UPET framework (sampling strategy, uncertainty, contrastive tuning, PEL, and robust loss function) and are ranked based on their perceived importance in demonstrating the value of the proposed techniques. The metrics should include both performance (as evaluated on downstream tasks) and efficiency (training time, parameter count) as highlighted in the paper's abstract.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Simple Sampling
- **Ablated Part**: Reliable Example Sampling (RES) mechanism (confidence + uncertainty)
- **Action**: REPLACE
- **Replacement**: 
  - Sampling based on confidence only
  - Random sampling from unlabeled data
- **Metrics**: Performance (e.g., Accuracy/F1), Efficiency (e.g., Training Time)

### Ablation: No Uncertainty in Sampling
- **Ablated Part**: Uncertainty estimation (MC Dropout) in Reliable Example Sampling
- **Action**: REMOVE
- **Metrics**: Performance (e.g., Accuracy/F1), Efficiency (e.g., Training Time)

### Ablation: No Contrastive Tuning
- **Ablated Part**: Easy-Hard Contrastive Tuning regularization
- **Action**: REMOVE
- **Metrics**: Performance (e.g., Accuracy/F1), Efficiency (e.g., Training Time)

### Ablation: Full Fine-tuning Student
- **Ablated Part**: Parameter-Efficient Learning (PEL) for student training
- **Action**: REPLACE
- **Replacement**: 
  - Full Fine-tuning
- **Metrics**: Performance (e.g., Accuracy/F1), Efficiency (e.g., Training Time, Trainable Parameters)

### Ablation: Standard Cross-Entropy Loss
- **Ablated Part**: Partially Huberised Cross-Entropy (PHCE) loss
- **Action**: REPLACE
- **Replacement**: 
  - Standard Cross-Entropy Loss
- **Metrics**: Performance (e.g., Accuracy/F1), Efficiency (e.g., Training Time)

</div>