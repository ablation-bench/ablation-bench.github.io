<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Basis_Function_Encoding_of_Numerical_Features_in_Factorization_Machines_for_Improved_Accuracy

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes using basis function encoding, specifically B-Splines, for numerical features in Factorization Machines (FM) variants. The core idea is to improve accuracy by allowing the model to learn smoother, segmentized functions of numerical features, overcoming the limitations of traditional binning (step functions and sparsity issues). The paper provides theoretical justification (spanning properties) and empirical evidence on synthetic data, public datasets, and an A/B test.

The existing experiments compare the proposed B-Spline encoding against traditional binning. On synthetic data, they show that B-Splines outperform binning, especially as the number of intervals/bins increases, where binning suffers from sparsity (Figure 4). On public datasets, they report the best tuned performance for Splines vs. Binning, showing improvements with Splines (Table 1). The A/B test confirms real-world performance gains.

While the comparison to binning is thorough, the paper's method has several key components that could be further investigated through ablation studies to understand their individual contributions and sensitivity:

1.  **The choice of B-Spline basis:** The paper advocates for B-Splines due to their approximation power and efficiency. However, it doesn't empirically compare B-Splines against other potential basis function types (e.g., polynomial basis, other spline degrees like linear splines, radial basis functions). An ablation study comparing different basis types would validate whether B-Splines are indeed the best choice or if similar gains could be achieved with simpler or alternative bases.
2.  **The number of basis functions:** The paper argues that B-Splines achieve good accuracy with a *small* number of basis functions, avoiding the sparsity issues of high-resolution binning. While Figure 4 shows the effect of the number of intervals on synthetic data for *both* methods, Table 1 only shows the *best* result for Splines on public datasets. A systematic study showing how the performance of the B-Spline method changes as the number of basis functions (or break-points) varies on the public datasets is missing. This would quantify the sensitivity to this hyperparameter and directly support the claim about needing only a small number of basis functions.

Based on their importance in validating the core claims and understanding the method's design choices, these two ablations are the most significant missing studies. The number of basis functions is arguably slightly more critical as it directly relates to the efficiency and sparsity claims central to the paper's motivation.

Therefore, I propose the following two missing ablation studies, ranked by importance:

1.  A study on the effect of varying the number of basis functions (break-points) used for the B-Spline encoding on the public datasets.
2.  A study comparing the performance of using B-Splines versus other common basis function types for encoding numerical features.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Effect of Number of Basis Functions
- **Ablated Part**: The number of basis functions (break-points) used for B-Spline encoding of numerical features.
- **Action**: REPLACE
- **Replacement**: 
  - 4
  - 8
  - 16
  - 32
  - 64
  - 128
- **Metrics**: RMSE, Cross-Entropy

### Comparison of Basis Function Types
- **Ablated Part**: The type of basis function used for encoding numerical features.
- **Action**: REPLACE
- **Replacement**: 
  - B-Splines (Degree 3)
  - Linear Splines (Degree 1)
  - Polynomial Basis (Degree 3)
- **Metrics**: RMSE, Cross-Entropy

</div>