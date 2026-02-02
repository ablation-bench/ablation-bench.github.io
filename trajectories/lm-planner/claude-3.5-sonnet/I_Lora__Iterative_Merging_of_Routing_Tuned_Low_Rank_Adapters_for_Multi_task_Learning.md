<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/I_Lora__Iterative_Merging_of_Routing_Tuned_Low_Rank_Adapters_for_Multi_task_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that while the authors conducted several ablation studies, there are some important missing ablations that could help better understand the method's key components. The paper's main contributions are:

1. Routing Tuning method - which uses different losses for task data vs general data
2. Iterative merging of LoRA adapters using SVD and maximization function

Looking at the existing ablations in the paper:
- They tested different SVD rank proportions (0.8 was chosen)
- They compared against other LoRA merging methods like TIES, DARE etc.
- They evaluated the epsilon parameters for different losses

However, I identify two critical missing ablation studies:

1. The impact of the loss components in Routing Tuning. The method uses both KL divergence loss and L2 norm loss on LoRA outputs, but there's no ablation showing their individual contributions.

2. The choice of maximization function for merging. While they justify it theoretically based on properties like equality and associativity, there's no empirical ablation comparing it to other merging functions that could satisfy similar properties.

I'll focus on these two as they represent core design choices that significantly impact the method's performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Loss Components Ablation
- **Ablated Part**: Loss components in Routing Tuning
- **Action**: REMOVE
- **Metrics**: task_performance, general_performance, reserve_rate

### Merging Function Ablation
- **Ablated Part**: Maximization function for merging
- **Action**: REPLACE
- **Replacement**: 
  - average
  - weighted_sum
  - element_wise_product
- **Metrics**: remaining_performance, mean_score, median_score

</div>