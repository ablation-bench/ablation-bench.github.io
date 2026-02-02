<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Boosting_Membership_Inference_Attacks_with_Upstream_Modification

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper clearly evaluates the impact of modifying the upstream steps (sampling bias by adjusting the drop rate and focusing on vulnerable points via outlier detection) and demonstrates that these modifications carry over to improve downstream attack performance. However, two important design choices in the combined modifications remain unanalyzed. First, in the combined pipeline the authors choose to sample only from the vulnerable points using a fixed drop rate (e.g., 50% drop on vulnerable points) without studying how sensitive the attack performance is to this parameter when applied exclusively on the vulnerable subset. Varying this drop rate could reveal an optimal trade-off between computational cost (number of partitions) and attack accuracy (e.g., TPR at zero FPR and AUC). Second, the combined method appends non‐vulnerable data to each partition obtained from vulnerable points. Although this design choice aims to preserve a “complete” picture of the data distribution, its benefit versus a potential dilution of the vulnerability signal has not been ablated. Removing the non‐vulnerable points from the partitions may lead to an even more focused analysis on the most leakage-prone data points, or it might hurt model generalization – a question that deserves further study. These two ablations would help isolate and quantify the contribution of each component in the upstream modification strategy.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation - Vulnerable Drop Rate Sensitivity
- **Ablated Part**: Drop rate used for partitioning the vulnerable (outlier) points in the combined modification pipeline
- **Action**: REPLACE
- **Replacement**: 
  - 50%
  - 40%
  - 30%
  - 20%
  - 10%
- **Metrics**: TPR@0% FPR, AUC

### Ablation - Non-Vulnerable Points Inclusion
- **Ablated Part**: Appending non-vulnerable (inlier) data to the vulnerable point partitions during shadow model training
- **Action**: REMOVE
- **Metrics**: TPR@0% FPR, AUC

</div>