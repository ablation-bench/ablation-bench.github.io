<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/mixup-amp

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, AMP consists of three main operations: Rand, Max, and Min operations. The key innovation is adding adversarial perturbation to the mixing coefficient λ rather than to the input examples. Here's my reasoning for the suggested ablation studies:

1. The most important ablation would be removing the adversarial perturbation (Max operation) entirely, since this is the core contribution. This would essentially reduce AMP to vanilla Mixup.

2. The second most important ablation would be testing different perturbation step sizes (ε), as this controls how much non-linearity is injected. The paper mentions this is a critical hyperparameter.

3. The Min operation uses a mask-based mechanism to select between losses. Testing without this mechanism would show its importance.

4. The mixing coefficient λ is sampled from a Beta distribution with parameter α. Testing different α values would show sensitivity to the interpolation policy.

5. The perturbation is only applied to the mixing coefficient for inputs, not labels. Testing perturbation on both would validate this design choice.

The key metrics used in the paper are error rate and performance under low-resource conditions.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Adversarial Perturbation
- **Ablated Part**: Max operation that adds adversarial perturbation to mixing coefficient
- **Action**: REMOVE
- **Metrics**: error_rate, low_resource_performance

### Perturbation Step Size
- **Ablated Part**: Step size epsilon for adversarial perturbation
- **Action**: REPLACE
- **Replacement**: 
  - 0.01
  - 0.05
  - 0.1
  - 0.2
- **Metrics**: error_rate, low_resource_performance

### No Loss Selection
- **Ablated Part**: Mask-based loss selection mechanism in Min operation
- **Action**: REMOVE
- **Metrics**: error_rate, low_resource_performance

### Beta Distribution
- **Ablated Part**: Alpha parameter of Beta distribution for sampling lambda
- **Action**: REPLACE
- **Replacement**: 
  - 0.2
  - 0.5
  - 1.0
  - 2.0
- **Metrics**: error_rate, low_resource_performance

### Label Perturbation
- **Ablated Part**: Adversarial perturbation application
- **Action**: ADD
- **Replacement**: 
  - apply_to_both_input_and_label_lambda
- **Metrics**: error_rate, low_resource_performance

</div>