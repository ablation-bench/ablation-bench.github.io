<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Detecting_Out_of_Distribution_Samples_via_Conditional_Distribution_Entropy_with_Optimal_Transport

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that the authors conducted ablation studies on several components:
1. Effect of temperature τ
2. Effect of contrastive training
3. Effect of training epochs
4. Effect of regularization coefficient λ
5. Effect of optimal transport

However, there are two important aspects that were not ablated:

1. The choice of cost matrix C in the optimal transport formulation. The authors use cosine distance but don't justify this choice compared to other distance metrics.

2. The choice of uniform weights for α and β in the empirical probability measures. The authors mention "For simplicity, we use uniform weights" but don't explore if other weighting schemes could improve performance.

These are important design choices that could significantly impact the method's performance. I'll suggest ablation studies for both.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Cost Matrix Ablation
- **Ablated Part**: Cost matrix C in optimal transport formulation
- **Action**: REPLACE
- **Replacement**: 
  - cosine distance
  - euclidean distance
  - manhattan distance
- **Metrics**: AUROC, AUPR, FPR

### Probability Measure Weights Ablation
- **Ablated Part**: Uniform weights α and β in empirical probability measures
- **Action**: REPLACE
- **Replacement**: 
  - uniform weights
  - class-balanced weights
  - distance-based weights
- **Metrics**: AUROC, AUPR, FPR

</div>