<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/foa

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Below is the ablation plan for FOA. The first ablation removes the back‐to‐source activation shifting mechanism to assess its contribution in aligning OOD activations to the source statistics. The second ablation studies the specially designed composite fitness function (which combines prediction entropy and activation statistics discrepancy) by replacing it with simpler alternatives (using only prediction entropy or only the statistics discrepancy). The third ablation removes the inserted prompt adaptation altogether to measure how critical the prompt update is for achieving test‐time adaptation without backpropagation. The fourth ablation replaces the chosen CMA evolution strategy with alternative derivative‐free optimizers (such as random search or Bayesian optimization) to determine if the choice of optimizer significantly affects the performance and adaptation latency. Lastly, the fifth ablation investigates the sensitivity of the prompt’s dimensionality (prompt length) by testing different sizes. Metrics such as accuracy (on benchmarks like ImageNet-C), memory usage, and even adaptation latency (for optimizer comparisons) are reported as in the original paper.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation-Back-to-Source
- **Ablated Part**: Back-to-source activation shifting mechanism that adjusts final-layer CLS features
- **Action**: REMOVE
- **Metrics**: accuracy, memory_usage

### Ablation-Fitness-Function
- **Ablated Part**: Composite unsupervised fitness function combining prediction entropy and distribution statistic discrepancy
- **Action**: REPLACE
- **Replacement**: 
  - prediction_entropy_only
  - statistics_discrepancy_only
- **Metrics**: accuracy

### Ablation-Prompt-Adaptation
- **Ablated Part**: Inserted prompt adaptation mechanism that enables forward-only model adaptation
- **Action**: REMOVE
- **Metrics**: accuracy

### Ablation-Optimizer-Choice
- **Ablated Part**: CMA evolution strategy used for optimizing the prompt
- **Action**: REPLACE
- **Replacement**: 
  - CMA_ES
  - random_search
  - bayesian_optimization
- **Metrics**: accuracy, adaptation_latency

### Ablation-Prompt-Length
- **Ablated Part**: Prompt embedding dimensionality (i.e., length of the inserted prompt)
- **Action**: REPLACE
- **Replacement**: 
  - small_length (5 tokens)
  - medium_length (10 tokens)
  - large_length (20 tokens)
- **Metrics**: accuracy

</div>