<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Boosting_Membership_Inference_Attacks_with_Upstream_Modification

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes modifications to the upstream stages of Membership Inference Attacks (MIAs), specifically focusing on two main components:

1. Sampling bias modification (Step 2): They reduce the drop rate during dataset partitioning from 50% to 10% to improve attack accuracy.

2. Attack aggregation modification (Step 4): They use outlier detection methods (specifically ApB - Accuracy per Batch) to identify vulnerable points instead of using the entire dataset.

The paper already includes ablations for:
- Different drop rates (50%, 40%, 30%, 20%, 10%)
- Different outlier detection methods (SPP, MD, ApB)
- Different number of shadow models (1 vs 100)

However, there are two important missing ablations:

1. The effect of the number of vulnerable points selected: The paper fixes this to 5,000 points but doesn't ablate this hyperparameter. This is crucial since it directly affects both the computational cost and attack effectiveness.

2. The robustness of the ApB outlier detection method: While ApB performs best, the paper doesn't ablate its key parameter - the frequency of accuracy measurement (currently done after each batch). This is important since it affects both computational overhead and outlier detection accuracy.

These ablations would provide important insights into the method's sensitivity to these key parameters.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Vulnerable Points Ablation
- **Ablated Part**: Number of vulnerable points selected for attack
- **Action**: REPLACE
- **Replacement**: 
  - 1000
  - 2500
  - 7500
  - 10000
- **Metrics**: TPR@FPR=0%, TPR@FPR=1%, AUC

### ApB Frequency Ablation
- **Ablated Part**: Frequency of accuracy measurement in ApB outlier detection
- **Action**: REPLACE
- **Replacement**: 
  - after each batch
  - after each epoch
  - after every 5 batches
  - after every 10 batches
- **Metrics**: TPR@FPR=0%, TPR@FPR=1%, AUC

</div>