<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Implicit_Functional_Bayesian_Deep_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The first missing ablation we suggest targets the core component of the proposed methods: the NTK‐based transformation of the BNN posterior to a Gaussian process. Although the paper compares the overall ifBNN/ifBDE methods to alternative approaches, it does not study in isolation how critical the NTK‐based GP transformation is. An ablation study that replaces this transformation with a standard deep network mean function based GP transformation (or even a setting that bypasses any GP transformation) would be valuable. This experiment would help quantify how much the NTK‐based implicit transformation contributes to the superior uncertainty estimation and predictive performance (as measured by RMSE, NLL, OOD-AUC, and classification accuracy where applicable).

The second missing ablation study focuses on the finite measurement set used to approximate the infinite-dimensional 2-Wasserstein distance between the transformed GP and the prior. The paper relies on this finite-sample approximation (which theoretically converges to the ideal distance), yet it does not investigate the sensitivity of performance when varying the number of measurement points. Testing different measurement set sizes (for example, small, medium, and large sample sizes) could reveal the trade-offs between computational cost and approximation accuracy, as observed through metrics such as RMSE and NLL.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### NTK-based GP Transformation Ablation
- **Ablated Part**: The implicit transformation of the BNN posterior to a Gaussian process using the Neural Tangent Kernel (NTK)
- **Action**: REPLACE
- **Replacement**: 
  - standard deep network mean GP transformation
  - direct use of BNN posterior without GP transformation
- **Metrics**: RMSE, Negative Log-Likelihood (NLL), OOD-AUC, Accuracy

### Measurement Set Size Ablation
- **Ablated Part**: The number of measurement points used to approximate the 2-Wasserstein distance between the GP transformed posterior and the functional prior
- **Action**: REPLACE
- **Replacement**: 
  - 10 points
  - 40 points
  - 80 points
- **Metrics**: RMSE, Negative Log-Likelihood (NLL)

</div>