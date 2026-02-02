<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Conformal_Prediction_Sets_with_Improved_Conditional_Coverage_using_Trust_Scores

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Conformal Prediction Sets with Improved Conditional Coverage using Trust Scores" introduces a method that enhances conditional coverage by utilizing classifier confidence and a nonparametric trust score. The existing ablation studies in the paper focus on comparing the proposed method (CONDITIONAL) with standard conformal prediction (STANDARD) and a naive baseline (NAIVE) across various datasets and metrics. The metrics used include marginal coverage, conditional coverage gap (CovGap) across different binning schemes, and average set size.

To identify missing ablation studies, we need to consider the core components of the proposed method: the use of trust scores and the specific function class used for achieving conditional coverage. The paper already evaluates the impact of different score functions (e.g., APS, RAPS) and compares the performance of the proposed method with other baselines. However, there are two potential areas for further ablation:

1. **Trust Score Component**: The trust score is a critical component of the method, serving as a proxy for the rank of the true class. An ablation study could explore the impact of removing the trust score or replacing it with alternative measures of model uncertainty, such as entropy or variance of the softmax outputs. This would help assess the importance of the trust score in achieving improved conditional coverage.

2. **Function Class Complexity**: The paper uses a polynomial function class to capture interactions between the conformity score and the variables Conf and Trust. An ablation study could investigate the effect of varying the complexity of this function class, such as using linear functions or higher-degree polynomials, to understand the trade-off between computational efficiency and coverage performance.

These ablation studies would provide insights into the robustness and flexibility of the proposed method and its reliance on specific components.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study on Trust Score
- **Ablated Part**: Trust score component used as a proxy for the rank of the true class
- **Action**: REPLACE
- **Replacement**: 
  - Entropy of softmax outputs
  - Variance of softmax outputs
- **Metrics**: Conf × Trust CovGap, Conf × Rank CovGap, Class-conditional CovGap, Average set size

### Ablation Study on Function Class Complexity
- **Ablated Part**: Polynomial function class used for capturing interactions
- **Action**: REPLACE
- **Replacement**: 
  - Linear function class
  - Higher-degree polynomial function class
- **Metrics**: Conf × Trust CovGap, Conf × Rank CovGap, Class-conditional CovGap, Average set size

</div>