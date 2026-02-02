<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/galore

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablations that target the most critical components of GaLore. The first experiment removes the multi‐subspace composition mechanism (i.e. the periodic re‐initialization of projection matrices) to test whether switching low‐rank subspaces is crucial for full-parameter training and memory efficiency. The second study replaces the fixed update frequency (T) for recomputing the projection matrices with various candidate values, to assess the tradeoffs between computational overhead, convergence speed, and final performance. The third experiment varies the projection rank (r) to understand its effect on both memory savings and gradient fidelity, which in turn impacts training convergence and downstream task performance. The fourth ablation compares different methods for generating the projection matrices (SVD-based versus random or learned projections) to gauge their impact on convergence speed and computational overhead. Finally, the fifth experiment studies the role of the scale factor (α) that governs the update magnitude in GaLore, as it is crucial for training stability and convergence. Together, these ablations will pinpoint which design choices most affect memory consumption, convergence rate, and overall model performance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Multi-Subspace Composition Ablation
- **Ablated Part**: Periodic re-initialization of projection matrices (switching low-rank subspaces)
- **Action**: REMOVE
- **Metrics**: convergence_rate, final_model_performance, optimizer_memory_usage

### Subspace Update Frequency Ablation
- **Ablated Part**: Frequency (T) of updating the projection matrices
- **Action**: REPLACE
- **Replacement**: 
  - 50
  - 100
  - 200
  - 500
  - 1000
- **Metrics**: convergence_rate, final_model_performance, training_overhead

### Projection Rank Ablation
- **Ablated Part**: Rank (r) of the projection matrices
- **Action**: REPLACE
- **Replacement**: 
  - 2
  - 4
  - 8
  - 16
- **Metrics**: validation_perplexity, glue_score, memory_consumption

### Projection Method Ablation
- **Ablated Part**: Method used to compute the projection matrices for gradient projection
- **Action**: REPLACE
- **Replacement**: 
  - SVD-based
  - Random Projection
  - Learned Projection
- **Metrics**: convergence_speed, final_model_performance, computational_overhead

### Scale Factor Ablation
- **Ablated Part**: Scale factor (α) controlling the strength of the low-rank update
- **Action**: REPLACE
- **Replacement**: 
  - 0.5
  - 1
  - 2
  - 4
- **Metrics**: training_stability, convergence_rate, final_model_performance

</div>