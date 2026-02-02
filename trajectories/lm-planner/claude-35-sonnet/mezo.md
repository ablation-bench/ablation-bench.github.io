<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/mezo

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, MeZO is a memory-efficient zeroth-order optimizer that adapts classical ZO-SGD to operate in-place for fine-tuning large language models. The key components that warrant ablation studies are:

1. The perturbation scale (ε) - This is a critical hyperparameter that affects the gradient estimation quality.

2. The number of random vectors (n) in n-SPSA - The paper uses n=1 by default but mentions this can be treated as a hyperparameter.

3. The in-place implementation - This is core to achieving memory efficiency.

4. The random seed resampling strategy - This is used to regenerate perturbation vectors without storing them.

5. The choice of optimizer - The paper mentions MeZO can be combined with other optimizers like Adam.

I'll prioritize testing the most important components that could significantly impact performance and memory usage.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Perturbation Scale Study
- **Ablated Part**: perturbation scale epsilon
- **Action**: REPLACE
- **Replacement**: 
  - 0.001
  - 0.01
  - 0.1
  - 1.0
- **Metrics**: accuracy, F1, memory usage

### SPSA Samples Study
- **Ablated Part**: number of random vectors n in n-SPSA
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 2
  - 4
  - 8
- **Metrics**: accuracy, F1, convergence rate

### Memory Implementation Study
- **Ablated Part**: in-place parameter updates
- **Action**: REPLACE
- **Replacement**: 
  - store full perturbation vector
  - store per-layer perturbations
- **Metrics**: memory usage, accuracy, training time

### Optimizer Comparison
- **Ablated Part**: base optimizer
- **Action**: REPLACE
- **Replacement**: 
  - SGD
  - SGD with momentum
  - Adam
- **Metrics**: accuracy, F1, convergence rate, memory usage

</div>