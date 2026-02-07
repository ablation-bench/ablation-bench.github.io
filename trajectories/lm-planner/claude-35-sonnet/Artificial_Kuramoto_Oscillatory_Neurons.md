<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Artificial_Kuramoto_Oscillatory_Neurons

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces Artificial Kuramoto Oscillatory Neurons (AKOrN) which uses oscillatory neurons and Kuramoto updates to bind features through synchronization. From analyzing the paper, I notice that:

1. The paper already includes ablations on:
- Projection operator (Proj) removal
- Conventional residual updates vs Kuramoto updates
- Number of rotating dimensions (N)
- Bias term C and norm-taking term m
- Symmetric vs asymmetric connections

2. However, I identify two important missing ablations:

First, the natural frequency term Ω plays a crucial role in preventing oscillators from getting stuck in bad minima (as shown in Section D.3.2), but there's no systematic ablation studying how different formulations of Ω affect performance across tasks.

Second, while the paper shows that increasing Kuramoto steps T improves performance, there's no ablation studying how different initialization schemes for the oscillators X affect convergence and final performance. This is important since the oscillators' initial state could significantly impact synchronization dynamics.

These ablations would provide deeper insights into the method's key mechanisms.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Natural Frequency Ablation
- **Ablated Part**: Natural frequency term Ω
- **Action**: REPLACE
- **Replacement**: 
  - zero matrix
  - random fixed matrix
  - learned diagonal matrix
  - full learned matrix
- **Metrics**: FG-ARI, MBO, Board Accuracy, Clean Accuracy, Adversarial Accuracy

### Oscillator Initialization Ablation
- **Ablated Part**: Initial oscillator states X(0)
- **Action**: REPLACE
- **Replacement**: 
  - random uniform on sphere
  - zeros + small noise
  - copy of conditional stimuli C
  - learned embedding
- **Metrics**: FG-ARI, MBO, Board Accuracy, Clean Accuracy, Adversarial Accuracy

</div>