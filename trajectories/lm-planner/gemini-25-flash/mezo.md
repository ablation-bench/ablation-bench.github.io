<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/mezo

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants a list of up to 5 important ablation studies for the paper "Fine-Tuning Language Models with Just Forward Passes". I need to identify key components of the MeZO method and propose variations (REMOVE, REPLACE, ADD) to understand their impact on performance and efficiency.

Based on the abstract and provided sections, the core of MeZO is the memory-efficient implementation of Zeroth-Order SGD (ZO-SGD) using the SPSA gradient estimator. Key aspects include:
1.  The SPSA gradient estimation itself, which involves perturbing parameters by a random vector $\vz$ and evaluating the loss at $\theta + \epsilon\vz$ and $\theta - \epsilon\vz$.
2.  The specific parameters of SPSA, namely the perturbation scale $\epsilon$ and the number of samples $n$.
3.  The memory-efficient implementation strategy (in-place perturbation and resampling $\vz$).
4.  Practical implementation details like perturbing matrices vs. individual parameters.
5.  The choice of SPSA over other potential ZO estimators.

I will propose ablation studies targeting these aspects, prioritizing those that investigate the core mechanism and its hyperparameters.

1.  **Perturbation Scale ($\epsilon$)**: This is a critical hyperparameter in SPSA that affects the gradient estimate's accuracy and noise. Varying this parameter is a standard and important ablation.
2.  **Number of SPSA Samples ($n$)**: The paper uses $n=1$ by default for efficiency but mentions $n$-SPSA. Increasing $n$ reduces variance but increases computation (more forward passes per step). Ablating this explores the trade-off.
3.  **Choice of ZO Estimator**: The paper chose SPSA. Comparing it to a different class of ZO estimators, like a one-point estimator, would validate this choice.
4.  **Perturbation Granularity**: The paper mentions perturbing matrices for speed. Ablating this to perturb individual parameters (if feasible) or smaller groups would test this implementation decision's impact.
5.  **Memory Efficiency Mechanism**: Ablating the in-place/resampling part would revert to a naive ZO-SGD. However, this might be impractical for large models due to memory constraints, which is precisely what MeZO aims to solve. While conceptually important, it might not be a feasible experiment on the scales where MeZO is most needed.

I will focus on the top 4 practical and impactful ablations. The metrics used in the paper include task-specific performance (Accuracy, F1, ROUGE), Memory usage, and GPU-hours. I will include these in the suggested ablations.

The final list of ablations, ranked by importance, will be:
1.  Varying the perturbation scale $\epsilon$.
2.  Varying the number of SPSA samples $n$.
3.  Replacing SPSA with a one-point estimator.
4.  Changing the granularity of parameter perturbation.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation_PerturbationScale
- **Ablated Part**: Perturbation scale (epsilon) in SPSA gradient estimation
- **Action**: REPLACE
- **Replacement**: 
  - 0.001
  - 0.0001
  - 1e-05
- **Metrics**: Task Performance (Accuracy/F1/ROUGE), Memory (GB), GPU-hours

### Ablation_NumberOfSPSASamples
- **Ablated Part**: Number of random vectors (n) used in n-SPSA
- **Action**: REPLACE
- **Replacement**: 
  - 2
  - 4
- **Metrics**: Task Performance (Accuracy/F1/ROUGE), Memory (GB), GPU-hours

### Ablation_ZOEstimator
- **Ablated Part**: SPSA gradient estimator
- **Action**: REPLACE
- **Replacement**: 
  - One-point ZO estimator (e.g., Zhang et al. 2022)
- **Metrics**: Task Performance (Accuracy/F1/ROUGE), Memory (GB), GPU-hours

### Ablation_PerturbationGranularity
- **Ablated Part**: Strategy for perturbing parameters (perturbing entire weight matrices)
- **Action**: REPLACE
- **Replacement**: 
  - Perturbing individual parameters
  - Perturbing smaller parameter blocks
- **Metrics**: Task Performance (Accuracy/F1/ROUGE), Memory (GB), GPU-hours

</div>