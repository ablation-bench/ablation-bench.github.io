<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Learning_with_Instance_Dependent_Label_Noise__Balancing_Accuracy_and_Fairness

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We observed that while the paper includes comprehensive experiments (varying alignment set size, noise rates, noise disparities, and an ablation study that decomposes the two-stage training) it did not isolate two core design choices. First, the auxiliary network ϕ uses the observed label as part of its input when computing the confidence score βˆ. It is not clear how much of the performance improvement and fairness balance is attributable to incorporating the observed label versus relying solely on the features (e.g., the pre-softmax outputs of θ). Ablating this input by either completely removing it or replacing it with a constant can shed light on its role. Second, the loss used in Step 2a weights each instance by a group-specific factor (the inverse of the estimated clean rate) to balance groups with different noise levels. Removing or replacing this re-weighting—using uniform weighting instead—would help quantify the impact of this component on both the overall discriminative performance (AUROC) and fairness (AUEOC). These two ablations are critical as they target the method’s major contributions in handling instance-dependent noise and fairness.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Exclude Observed Label from Auxiliary Network
- **Ablated Part**: The input to the auxiliary network ϕ that includes the observed label (y˜) used to compute the confidence score βˆϕ
- **Action**: REPLACE
- **Replacement**: 
  - Remove the observed label input (feed only the pre-softmax output of θ)
  - Replace the observed label input with a constant indicator
- **Metrics**: AUROC, AUEOC

### Ablation: Remove Group-Specific Loss Re-weighting
- **Ablated Part**: The group-specific re-weighting mechanism in the loss L′θ that scales each instance’s loss by 1/(1−rˆ) to account for varying clean rates across subgroups
- **Action**: REMOVE
- **Metrics**: AUROC, AUEOC

</div>