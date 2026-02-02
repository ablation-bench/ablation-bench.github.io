<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Boosting_Membership_Inference_Attacks_with_Upstream_Modification

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Boosting Membership Inference Attacks with Upstream Modification" proposes improvements to the shadow model framework for Membership Inference Attacks (MIAs), specifically targeting the scenario where the model owner acts as the attacker with full data knowledge but limited computational budget. The core contributions are modifications to the upstream stages: addressing sampling bias by using a low drop rate during data partitioning and addressing attack aggregation by focusing the attack on the most vulnerable points (identified as outliers).

The paper demonstrates that using a lower drop rate improves attack success (Section 3.1) and that attacking only outliers significantly boosts performance compared to attacking random points (Section 3.2), with ApB being the most effective outlier detection method among those tested. The combined method (Section 4) leverages ApB to identify outliers, samples data partitions *only* from these outliers (plus non-outliers) using a low drop rate, and then runs the MIA *only* on the identified outliers. The evaluation shows that this combined approach drastically improves MIA performance, often outperforming the original framework with significantly fewer shadow models.

The paper includes several relevant evaluations: the effect of drop rate, the benefit of attacking outliers, a comparison of different outlier detection methods, and the overall performance of the combined method against the original framework.

However, two important ablation studies are missing:

1.  **Sensitivity of the Combined Method to the Number of Outliers:** The paper shows that attacking a smaller set of top outliers yields better results than attacking random points (Table 2). It also evaluates the *combined* method using a fixed number of 5,000 outliers (Section 4). A crucial missing piece is understanding how the performance of the *full combined pipeline* (outlier detection, outlier-based sampling, outlier attack) changes as the number of top outliers selected varies. This is vital for practical application, as a model owner needs to know how many points they can reliably identify as members and how the attack performance scales with the size of the targeted set. Evaluating the combined method with different numbers of outliers would provide this insight.

2.  **Disentangling the Contribution of Outlier-Based Sampling:** The combined method modifies both sampling (low drop rate applied specifically to outliers) and aggregation (attacking only outliers). Section 3.2 shows the benefit of attacking outliers. Section 3.1 shows the benefit of a low drop rate in general. The combined method's sampling strategy is unique in that it samples *from outliers* with a low drop rate to keep the number of partitions low. It's not fully clear from the existing experiments how much of the combined method's success is due specifically to this outlier-based sampling strategy, independent of the benefit gained simply by attacking outliers. An ablation comparing the combined method (outlier sampling + outlier attack) against a variant that uses the original sampling strategy (e.g., 50% drop on the full dataset) but still attacks only the ApB-identified outliers would isolate the contribution of the novel sampling approach.

Ranking these, the sensitivity to the number of outliers in the combined method is arguably slightly more important for practical deployment and understanding the method's limits and trade-offs. Disentangling the sampling strategy is more about understanding the specific mechanism of the proposed method's improvement. Therefore, I will suggest the sensitivity analysis first.

Both suggested ablations should use the metrics reported in the paper, primarily AUC and TPR at low FPRs (0% and 1%).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Sensitivity to Number of Outliers (Combined Method)
- **Ablated Part**: Number of top outliers used for sampling and attack in the combined method
- **Action**: REPLACE
- **Replacement**: 
  - 1250
  - 2500
  - 5000
  - 10000
  - 20000
- **Metrics**: AUC, TPR@FPR 0%, TPR@FPR 1%

### Contribution of Outlier-Based Sampling
- **Ablated Part**: Data partitioning strategy in the combined method
- **Action**: REPLACE
- **Replacement**: 
  - Outlier-based sampling (as in paper)
  - Original sampling (e.g., 50% drop on full dataset)
- **Metrics**: AUC, TPR@FPR 0%, TPR@FPR 1%

</div>