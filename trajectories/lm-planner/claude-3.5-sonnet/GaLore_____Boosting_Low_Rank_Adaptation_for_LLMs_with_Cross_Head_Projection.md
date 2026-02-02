<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/GaLore_____Boosting_Low_Rank_Adaptation_for_LLMs_with_Cross_Head_Projection

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces GaLore+, which improves upon GaLore by:
1. Using cross-head low-rank projection to reduce SVD computation time
2. Employing randomized subspace iteration for faster SVD
3. Using sparsely coded residuals to reduce approximation errors

The paper already includes ablation studies on:
- The proportion of non-zero elements in sparse indexing matrix (Section 5.3)

However, there are two important components that lack proper ablation studies:

1. The cross-head projection sharing mechanism is a major contribution but there's no ablation showing its impact on model quality vs computational gains. While Figure 2b shows approximation errors, there's no direct study of how this affects final model performance.

2. The randomized subspace iteration for SVD is introduced as a key optimization but there's no ablation studying the trade-off between speed and accuracy compared to regular SVD. While the paper claims computational benefits, the impact on model quality is not isolated.

These would be the most important missing ablations since they relate to the two main technical contributions that differentiate GaLore+ from GaLore.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Cross-head Projection Ablation
- **Ablated Part**: cross-head projection sharing in multi-head attention
- **Action**: REPLACE
- **Replacement**: 
  - no sharing (separate projection per head)
  - partial sharing (share only between pairs of heads)
  - full sharing (proposed method)
- **Metrics**: accuracy, BLEU, ROUGE-1/2/L, CIDEr, training time, memory usage

### SVD Method Ablation
- **Ablated Part**: randomized subspace iteration for SVD
- **Action**: REPLACE
- **Replacement**: 
  - regular SVD
  - randomized SVD with different iteration counts (1,2,4,8)
- **Metrics**: accuracy, BLEU, ROUGE-1/2/L, CIDEr, training time, SVD computation time

</div>