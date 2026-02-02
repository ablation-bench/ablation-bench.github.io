<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Effective_Text_to_Image_Alignment_with_Quality_Aware_Pair_Ranking

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper conducts extensive ablations on scoring models, fine-tuning methods, and LoRA rank, showing improvements when using a quality-sorted subset of data. However, one critical component that has not been isolated is the formulation of the quality metric itself. The current metric is defined as ψ(xw/c) * (1 - ψ(xl/c)), but it is unclear if this particular combination is optimal. An ablation study comparing alternative formulations—such as a difference-based metric (ψ(xw/c) - ψ(xl/c)) or a ratio-based metric—could help determine the most effective way to capture pair quality.
Additionally, the paper selects a fixed top 5.33% of data based on quality ranking, but it does not explore the potential benefits of dynamically adjusting this threshold. An experiment in which the fixed threshold is replaced with a dynamic threshold (e.g., based on the distribution of quality scores or validation performance) could reveal if an adaptive data selection strategy might yield even better alignment results.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Quality Metric Formulation Ablation
- **Ablated Part**: The formulation of the quality metric used to rank image preference pairs (currently ψ(xw/c) * (1 - ψ(xl/c)))
- **Action**: REPLACE
- **Replacement**: 
  - Difference-based metric: ψ(xw/c) - ψ(xl/c)
  - Ratio-based metric: ψ(xw/c) / (ψ(xl/c) + ε)
- **Metrics**: Aesthetic Score, Image Reward, PickScore, HPSv2

### Dynamic Thresholding Ablation
- **Ablated Part**: The fixed top 5.33% data selection strategy for fine-tuning
- **Action**: REPLACE
- **Replacement**: 
  - Dynamic percentile thresholding based on the quality score distribution
  - Adaptive thresholding using validation performance
- **Metrics**: Aesthetic Score, Image Reward, PickScore, HPSv2

</div>