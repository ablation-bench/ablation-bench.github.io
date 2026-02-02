<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Improving_Robustness_and_Accuracy_with_Retrospective_Online_Adversarial_Distillation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Improving Robustness and Accuracy with Retrospective Online Adversarial Distillation" introduces a novel method called ROAD, which aims to improve both robustness and natural accuracy of models against adversarial attacks. The method leverages self-adversarial distillation from the last epoch and collaborative learning with a natural model. The paper includes several ablation studies to evaluate the impact of different components of ROAD, such as the effect of different scheduling strategies for the interpolation ratio, the impact of asymmetric knowledge transfer, and the role of soft labels.

However, there are a few potential areas where additional ablation studies could provide further insights:

1. **Impact of the Natural Model's Architecture**: The paper mentions the use of a natural model trained collaboratively with the robust model. An ablation study could explore the impact of using different architectures for the natural model. This would help understand if the choice of architecture for the natural model significantly affects the robustness and accuracy of the robust model.

2. **Effect of Varying the Interpolation Ratio Schedule**: While the paper explores different scheduling strategies for the interpolation ratio, it does not investigate the effect of varying the final value of the interpolation ratio. An ablation study could examine how different final values of the interpolation ratio affect the performance of the model, providing insights into the sensitivity of the method to this hyperparameter.

These ablation studies would help in understanding the sensitivity of the ROAD method to different design choices and hyperparameters, potentially leading to further improvements in its performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Architecture of the natural model
- **Action**: REPLACE
- **Replacement**: 
  - ResNet-18
  - MobileNetV2
  - WRN-28-10
- **Metrics**: NAT, PGD-20, PGD-100, MIM-10, AA

### Ablation Study 2
- **Ablated Part**: Final value of the interpolation ratio
- **Action**: REPLACE
- **Replacement**: 
  - 0.6
  - 0.8
  - 1.0
- **Metrics**: NAT, PGD-20, PGD-100, MIM-10, AA

</div>