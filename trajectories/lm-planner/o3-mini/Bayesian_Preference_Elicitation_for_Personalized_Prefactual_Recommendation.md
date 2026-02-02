<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Bayesian_Preference_Elicitation_for_Personalized_Prefactual_Recommendation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We suggest two key ablation experiments that were not included in the paper. The first one focuses on the question selection mechanism. In the method the authors use a mutual‐information–maximization criterion to choose the pairwise comparison questions for elicitation. It would be insightful to replace this mechanism with alternative strategies – for example a random selection of question pairs or one based directly on the cost difference between candidate pairs – and then compare the resulting recourse quality. Reporting metrics such as the overall cost of the recommended recourse (e.g., Mahalanobis cost), recourse validity (i.e. whether the recommended recourse yields a positive prediction), and the mean rank performance, would quantify the value added by the mutual information strategy.
 
The second ablation targets the Bayesian posterior update procedure. The framework uses a sophisticated posterior update via a projected gradient descent algorithm to refine the prior on the cost function parameters. An ablation study that replaces this update with a “no update” strategy (i.e. fixing the prior) or with a simpler update method (like standard gradient descent without the projection step) would help measure the impact of the update procedure on the personalized recourse recommendations. Again, key metrics such as recourse cost, validity, and even the convergence speed or stability of the update process would be informative.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Question Selection Strategy
- **Ablated Part**: The mutual-information maximization question selection mechanism used for eliciting user cost preferences
- **Action**: REPLACE
- **Replacement**: 
  - random question selection
  - cost-difference based selection
- **Metrics**: Cost, Validity, Mean Rank Performance

### Ablation: Posterior Update Mechanism
- **Ablated Part**: The Bayesian posterior update via the projected gradient descent algorithm for refining the cost weighting matrix
- **Action**: REPLACE
- **Replacement**: 
  - fixed prior (no update)
  - standard gradient descent update without projection
- **Metrics**: Cost, Validity, Convergence Speed

</div>