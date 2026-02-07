<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Active_Fine_Tuning_of_Generalist_Policies

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes AMF (Active Multi-task Fine-tuning) for selecting informative demonstrations to fine-tune pre-trained policies. Looking at the method and experiments, I identify two key missing ablations:

1. Alternative Information Gain Measures: The paper uses mutual information as the criterion for selecting tasks, but does not ablate this choice against other information-theoretic measures like entropy reduction or KL divergence. This is important since the choice of information measure could significantly impact task selection.

2. Trajectory Length Impact: The paper uses fixed trajectory lengths (H) for demonstrations but does not study how varying this hyperparameter affects performance. Since longer trajectories provide more supervision but may be more costly to obtain, understanding this trade-off is crucial for practical applications.

The paper already ablates uncertainty estimation methods, batch sizes, and pre-training distributions, but these two aspects remain unexplored despite being fundamental design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Alternative Information Measures
- **Ablated Part**: Mutual information criterion for task selection
- **Action**: REPLACE
- **Replacement**: 
  - Entropy reduction
  - KL divergence
  - Jensen-Shannon divergence
- **Metrics**: Multi-task success rate, Area under success rate curve

### Trajectory Length Analysis
- **Ablated Part**: Fixed trajectory length H
- **Action**: REPLACE
- **Replacement**: 
  - H/2
  - 2H
  - 4H
- **Metrics**: Multi-task success rate, Area under success rate curve, Sample efficiency (success rate vs total timesteps)

</div>