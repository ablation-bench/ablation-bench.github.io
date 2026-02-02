<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/A_General_Framework_for_Off_Policy_Learning_with_Partially_Observed_Reward

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One important component of HyPeR is how it leverages secondary rewards to reduce the variance of the policy gradient estimator. In the paper the secondary rewards are aggregated via a function F(s) (e.g. a weighted linear function) to imitate the target reward. However, the paper does not study the sensitivity of the method to the choice of F(s). Investigating different aggregation functions (e.g. simple mean, an identity mapping, or a non‐linear MLP aggregator) would reveal whether the performance of HyPeR is robust to this design choice. 

A second potential missing ablation focuses on the q-function estimation modules. HyPeR depends on two estimators: one that predicts the expected target reward q(x,a) from partially observed rewards and another that leverages the secondary rewards q(x,a,s) for variance reduction. The quality of these regression models is critical to achieving unbiasedness and low variance. An ablation study comparing different regression models (e.g., linear regression versus non-linear estimators versus an oracle estimator) for both qˆ(x,a) and qˆ(x,a,s) could provide valuable insights on how sensitive HyPeR’s performance is to the accuracy of these components. The evaluation metrics should remain consistent with those used in the paper (combined policy value, target policy value, and secondary policy value) across synthetic and real-world datasets.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Secondary Reward Aggregation Function
- **Ablated Part**: The aggregation function F(s) that combines the secondary rewards to mimic the target reward in the hybrid policy gradient estimator
- **Action**: REPLACE
- **Replacement**: 
  - weighted average (default)
  - simple mean
  - identity function
  - non-linear MLP
- **Metrics**: combined policy value, target policy value, secondary policy value

### Ablation: Q-function Estimation Strategy
- **Ablated Part**: The regression module that estimates the q-functions (qˆ(x,a) and qˆ(x,a,s)) used in the policy gradient estimator
- **Action**: REPLACE
- **Replacement**: 
  - linear regression
  - non-linear regression (MLP)
  - oracle estimator
- **Metrics**: combined policy value, target policy value, secondary policy value

</div>