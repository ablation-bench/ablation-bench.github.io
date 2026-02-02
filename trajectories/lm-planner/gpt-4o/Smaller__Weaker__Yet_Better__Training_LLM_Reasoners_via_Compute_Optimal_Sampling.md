<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Smaller__Weaker__Yet_Better__Training_LLM_Reasoners_via_Compute_Optimal_Sampling

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Smaller, Weaker, Yet Better: Training LLM Reasoners via Compute-Optimal Sampling" explores the trade-offs between using stronger, more expensive models (SE) and weaker, cheaper models (WC) for generating synthetic data to train language models (LMs). The authors demonstrate that WC-generated data can be more compute-optimal than SE-generated data, challenging the prevailing practice of relying on SE models for synthetic data generation. The paper includes several ablation studies, such as the impact of dataset size, sampling strategy, and the role of quality dimensions (coverage, diversity, and false positive rate) on model performance.

However, there are a few potential missing ablation studies that could further elucidate the findings:

1. **Ablation of the Filtering Mechanism**: The paper mentions filtering incorrect solutions based on final answer correctness. An ablation study could explore the impact of different filtering mechanisms on the quality of the synthetic data and the performance of the finetuned models. This could include comparing the current filtering method with alternative approaches, such as process-based or outcome-based reward models.

2. **Ablation of the Weak-to-Strong Improvement Paradigm**: The paper introduces a novel weak-to-strong improvement setup, where a weaker LM teaches reasoning to a stronger LM. An ablation study could investigate the impact of this paradigm by comparing it with traditional knowledge distillation and self-improvement setups. This could involve removing the weak-to-strong improvement setup and observing the changes in model performance.

These ablations would provide insights into the robustness and generalizability of the proposed method and help identify the key factors contributing to its success.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Filtering Mechanism
- **Ablated Part**: Filtering mechanism based on final answer correctness
- **Action**: REPLACE
- **Replacement**: 
  - Process-based filtering
  - Outcome-based reward model
- **Metrics**: coverage, diversity, false positive rate, pass@1 accuracy

### Ablation of Weak-to-Strong Improvement
- **Ablated Part**: Weak-to-strong improvement setup
- **Action**: REMOVE
- **Metrics**: pass@1 accuracy, maj@k accuracy

</div>