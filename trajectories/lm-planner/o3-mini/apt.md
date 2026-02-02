<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/apt

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Below is our ablation plan to disentangle the contributions of each major component of APT. Our highest‐priority studies focus on isolating the adaptive pruning and tuning modules – the two core innovations of the method – to measure their impact on both training/inference efficiency and task performance. Next, we assess the supporting techniques: the self-knowledge distillation module that aids performance recovery after pruning, the outlier-aware salience scoring that improves the selection of parameters to prune, and finally the dynamic (versus fixed) adapter rank adaptation strategy within the APT adapter. For each ablation we propose either to REMOVE the component (to test its necessity) or to REPLACE it (with a simpler or fixed alternative), while tracking metrics used in the paper such as task performance (accuracy), training convergence time, peak training memory, inference latency, and inference memory consumption.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Remove Adaptive Pruning
- **Ablated Part**: The adaptive pruning module that uses binary masks informed by outlier-aware salience scores to remove unimportant LM parameter blocks
- **Action**: REMOVE
- **Metrics**: task_performance, training_time, training_memory, inference_time, inference_memory

### Ablation 2: Remove Adaptive Tuning
- **Ablated Part**: The adaptive tuning module which dynamically increases APT adapter ranks in task-sensitive layers
- **Action**: REMOVE
- **Metrics**: task_performance, training_time, training_memory, inference_time, inference_memory

### Ablation 3: Remove Self-Knowledge Distillation
- **Ablated Part**: The efficient self-knowledge distillation technique used to recover pruned LM performance
- **Action**: REMOVE
- **Metrics**: task_performance, training_convergence, training_memory

### Ablation 4: Replace Outlier-Aware Salience Scoring
- **Ablated Part**: The outlier-aware salience scoring function (which combines activation-gradient product with kurtosis) for selecting pruning blocks
- **Action**: REPLACE
- **Replacement**: 
  - standard salience scoring using only weight-gradient product
- **Metrics**: task_performance, pruning accuracy, training_time

### Ablation 5: Fixed Adapter Rank
- **Ablated Part**: The dynamic rank adaptation in APT adapters that increases tuning parameters based on layer importance
- **Action**: REPLACE
- **Replacement**: 
  - static adapter rank at fixed values (e.g., r=4, r=8, r=16)
- **Metrics**: task_performance, training_convergence, training_memory

</div>