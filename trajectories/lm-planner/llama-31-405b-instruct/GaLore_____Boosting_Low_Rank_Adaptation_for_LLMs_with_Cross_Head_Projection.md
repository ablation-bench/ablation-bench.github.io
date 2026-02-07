<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/GaLore_____Boosting_Low_Rank_Adaptation_for_LLMs_with_Cross_Head_Projection

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes GaLore+, a low-rank adaptation method with fast yet precise estimation of the low-rank projections. The estimation is achieved by cross-head low-rank projection and randomized subspace iteration. The authors also employ a sparsely coded residual to further reduce the error of low-rank approximation, which works on the moments of the optimizer. The experiments on arithmetic reasoning and natural language generation indicate that GaLore+ outperforms existing low-rank adaptation methods, offering superior performance with reduced computational complexity.

To further investigate the effectiveness of GaLore+, we suggest two missing ablation studies:

1. Investigating the impact of different low-rank settings on the performance of GaLore+. The authors only report results for a fixed low-rank setting (r = 32). It would be interesting to see how the performance of GaLore+ changes with different low-rank settings.

2. Analyzing the effect of the sparsely coded residual on the performance of GaLore+. The authors report results with and without the sparsely coded residual, but it would be interesting to see how the performance of GaLore+ changes with different proportions of non-zero elements in the sparse indexing matrix.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: low-rank setting
- **Action**: REPLACE
- **Replacement**: 
  - 16
  - 32
  - 64
  - 128
- **Metrics**: accuracy, fine-tuning time

### Ablation Study 2
- **Ablated Part**: sparsely coded residual
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.6
  - 1.2
  - 1.8
- **Metrics**: accuracy, fine-tuning time

</div>