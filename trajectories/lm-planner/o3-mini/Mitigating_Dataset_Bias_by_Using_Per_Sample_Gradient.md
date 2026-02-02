<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Mitigating_Dataset_Bias_by_Using_Per_Sample_Gradient

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The first missing ablation study we suggest is to examine how the source of the per‐sample gradient affects the oversampling strategy. In PGD the sampling probabilities are computed using gradients from the biased model. However, it is unclear whether using gradients computed from the debiased model (or an ensemble of both) would yield similar or different debiasing benefits. This ablation is critical to validate the design choice that the biased model’s gradient is essential for flagging bias‐conflicting samples. We propose replacing the biased‐model gradient with alternative sources and comparing public metrics such as unbiased test accuracy, overall test accuracy, and worst‐group accuracy.

The second missing ablation study is to investigate from which layer the per‐sample gradients should be extracted. The paper mentions that for computational efficiency the gradient is computed only from the final fully-connected (FC) layer. However, gradients from earlier layers (e.g. the penultimate layer) or even the full network gradient might encode richer information about sample difficulty and bias. An ablation study that replaces the “final FC layer only” extraction with variants (penultimate layer or full model gradients) can clarify the tradeoffs between performance and computational overhead. The metrics to report include unbiased test accuracy, overall test accuracy, and computational cost.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Gradient Source Ablation
- **Ablated Part**: The sampling probability computation that uses per-sample gradient information; currently, the gradient is computed from the biased model.
- **Action**: REPLACE
- **Replacement**: 
  - biased model gradient (baseline)
  - debiased model gradient
  - ensemble of biased and debiased gradients
- **Metrics**: unbiased test accuracy, overall test accuracy, worst-group accuracy

### Gradient Extraction Layer Ablation
- **Ablated Part**: The component that extracts the per-sample gradient, which currently uses only the final fully-connected layer's gradient.
- **Action**: REPLACE
- **Replacement**: 
  - final FC layer (baseline)
  - penultimate layer
  - full network gradient
- **Metrics**: unbiased test accuracy, overall test accuracy, computational cost

</div>