<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/mezo

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The following ablation studies focus on key design components of MeZO. First, we investigate the effect of the number of SPSA samples (n) used in the gradient estimate. Since the estimator’s quality and the allowable learning rate depend on n (as highlighted in Lemma 2 and the discussion around Eq. (1)), trying different values (for instance 1, 4, or 8) will help clarify the trade-off between gradient variance and convergence speed. Second, we study the sensitivity of MeZO to the perturbation scale (ε) used in SPSA; as ε controls the finite-difference approximation quality, its tuning is critical for both stability and performance. Third, we propose to remove the memory-efficient in-place update mechanism (the seed-based regeneration of Gaussian noise instead of storing full vectors) so that we can contrast the memory footprint and runtime efficiency of the proposed method with a standard ZO implementation. Fourth, MeZO claims compatibility with parameter-efficient fine-tuning (PEFT) techniques such as LoRA and prefix tuning; thus, we examine replacing full-parameter updates with these PEFT alternatives to assess their impact on performance and resource efficiency. Lastly, we compare SPSA with an alternate one‐point gradient estimator, to determine whether SPSA indeed strikes the best balance between estimation quality and computational overhead. For each ablation, we propose to report the metrics used in the paper such as accuracy, F1 score, convergence rate (or iteration count), GPU-hour consumption, and memory footprint where applicable.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A: SPSA Sample Size
- **Ablated Part**: Number of SPSA samples (n) used for gradient estimation
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 4
  - 8
- **Metrics**: accuracy, F1, convergence rate, GPU-hours

### Ablation B: Perturbation Scale Sensitivity
- **Ablated Part**: Perturbation scale (epsilon) in the SPSA gradient approximation
- **Action**: REPLACE
- **Replacement**: 
  - 1e-3
  - 1e-4
  - 1e-5
- **Metrics**: accuracy, F1, stability, convergence rate

### Ablation C: Memory-Efficient Mechanism
- **Ablated Part**: In-place parameter perturbation mechanism (seed-based noise regeneration)
- **Action**: REMOVE
- **Metrics**: memory footprint, training speed, accuracy

### Ablation D: PEFT Variants
- **Ablated Part**: Tuning strategy by replacing full-parameter updates with parameter-efficient methods
- **Action**: REPLACE
- **Replacement**: 
  - LoRA
  - Prefix Tuning
- **Metrics**: accuracy, memory reduction, GPU-hours

### Ablation E: Gradient Estimator Choice
- **Ablated Part**: Gradient estimation method used in MeZO
- **Action**: REPLACE
- **Replacement**: 
  - SPSA
  - One-point estimator
- **Metrics**: accuracy, F1, convergence rate, forward pass count

</div>