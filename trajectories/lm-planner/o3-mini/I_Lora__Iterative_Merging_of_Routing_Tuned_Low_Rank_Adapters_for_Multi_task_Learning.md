<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/I_Lora__Iterative_Merging_of_Routing_Tuned_Low_Rank_Adapters_for_Multi_task_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces two major components: Routing Tuning and Iterative Merging. In routing tuning, the method uses a composite loss function with a KL divergence term and an L2 norm term to (a) align the adapter‐augmented outputs with the base model outputs on general data and (b) drive the LoRA activations toward zero when non–task-specific inputs are processed. However, the paper does not provide an ablation that isolates the contribution of each loss component. Removing one component (e.g. the KL divergence loss) would reveal its unique impact on maintaining generalization and task performance. This is crucial given that the routing tuning loss is central to preserving the original model’s capabilities while adapting to new tasks.

Another key component is the iterative merging mechanism for combining LoRA adapters. The method employs SVD to reduce redundancy and chooses to retain 80% of the singular values during merging. Although the authors mention that the proportion saved did not show a strong pattern of influence, a systematic investigation (testing thresholds such as 0.7, 0.8, and 0.9) could provide deeper insights on the sensitivity of iterative merging performance relative to the choice of retained singular value proportion.

Thus, the two most important missing ablation studies are: (1) a breakdown of routing tuning loss by removing the KL divergence component, and (2) a sensitivity study on the SVD retention ratio during iterative merging.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### KL Divergence Loss Ablation
- **Ablated Part**: The KL divergence loss component in the Routing Tuning strategy that enforces consistency between the base model and the LoRA-augmented outputs on general data
- **Action**: REMOVE
- **Metrics**: mean_human_normalized_score, generalization_retention_rate

### SVD Retention Ratio Sensitivity
- **Ablated Part**: The proportion of singular values retained during the SVD step in iterative merging of LoRA adapters
- **Action**: REPLACE
- **Replacement**: 
  - 0.7
  - 0.8
  - 0.9
- **Metrics**: degradation_ratio, remaining_performance

</div>