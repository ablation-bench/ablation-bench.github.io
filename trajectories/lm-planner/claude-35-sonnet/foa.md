<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/foa

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents FOA, which has two main components:
1. Forward-Only Prompt Adaptation using CMA-ES optimization
2. Back-to-Source Activation Shifting

The key innovations that should be tested through ablations are:

1. The fitness function which combines entropy and statistics discrepancy - this is crucial for the CMA optimization to work properly.

2. The prompt adaptation approach - testing if this is better than directly trying to optimize model parameters.

3. The activation shifting mechanism - verifying its contribution to performance.

4. The CMA-ES optimizer choice - comparing against other derivative-free optimization approaches.

5. The combination of both prompt adaptation and activation shifting - understanding if they complement each other.

I'll suggest ablations focused on these key aspects, ranked by importance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Fitness Function Components
- **Ablated Part**: The fitness function components (entropy and statistics discrepancy)
- **Action**: REPLACE
- **Replacement**: 
  - only entropy term
  - only statistics discrepancy term
- **Metrics**: accuracy, ECE

### Activation Shifting
- **Ablated Part**: Back-to-source activation shifting mechanism
- **Action**: REMOVE
- **Metrics**: accuracy, ECE

### Optimizer Choice
- **Ablated Part**: CMA-ES optimizer
- **Action**: REPLACE
- **Replacement**: 
  - random search
  - Bayesian optimization
  - evolution strategies
- **Metrics**: accuracy, memory usage, adaptation time

### Prompt Location
- **Ablated Part**: Input-level prompt placement
- **Action**: REPLACE
- **Replacement**: 
  - middle-layer prompts
  - output-layer prompts
- **Metrics**: accuracy, memory usage

### Statistics Collection
- **Ablated Part**: Number of source samples for statistics calculation
- **Action**: REPLACE
- **Replacement**: 
  - 8 samples
  - 16 samples
  - 64 samples
  - 128 samples
- **Metrics**: accuracy, memory usage

</div>