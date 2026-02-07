<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Implicit_Functional_Bayesian_Deep_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Implicit Functional Bayesian Deep Learning" proposes two novel methods, ifBNN and ifBDE, which leverage the Neural Tangent Kernel (NTK) to implicitly transform BDL posteriors to Gaussian Processes (GPs) and use the 2-Wasserstein distance for functional inference. The core ideas involve the NTK-based GP transformation and, for ifBDE, the use of the Wasserstein Barycenter to aggregate the ensemble members' GP transformations.

The paper compares the proposed methods against several existing weight-space and function-space BDL approaches (KLBNN, WBNN, BDE, fBNN, FSVI, GWI). The comparison with GWI is particularly relevant as GWI also uses the 2-Wasserstein distance but relies on a different, simpler GP approximation of the BDL posterior, which the authors argue reduces uncertainty modeling capability. This comparison serves as an indirect evaluation of the NTK-based transformation's benefit.

However, the paper lacks dedicated ablation studies that isolate the contribution of specific components *within* the proposed ifBDL framework. Two key components stand out as candidates for missing ablations:

1.  **The Wasserstein Barycenter in ifBDE:** Section 3.2 introduces the Wasserstein Barycenter as a method to aggregate the GP transformations of the ensemble members, contrasting it with a "straightforward average" (Equation 19). While the theoretical motivation for the barycenter is provided, the paper does not present experimental results comparing ifBDE using the Wasserstein Barycenter versus ifBDE using the simple average. This ablation would directly demonstrate the empirical benefit (or lack thereof) of using the more complex barycenter aggregation.
2.  **The NTK-based GP Transformation:** The NTK-based transformation (Equation 14 for ifBNN, Equation 20 for ifBDE members) is central to enabling the tractable 2-Wasserstein distance computation while aiming to preserve BDL capabilities. An ablation could replace this specific NTK-derived GP approximation with a simpler GP approximation on the finite measurement set, similar in spirit to the degeneration used in GWI (e.g., approximating the posterior on the measurement set as a Gaussian with a learned diagonal covariance or even a fixed covariance), but applied *within* the ifBNN or ifBDE framework. Ablating this in ifBNN would be cleaner as it avoids the additional complexity of ensemble aggregation. This would help quantify the specific benefit of the NTK derivation compared to a simpler Gaussian approximation on the measurement points.

Based on their importance and the lack of direct evaluation in the paper, I propose these two missing ablation studies. The first ablation (Barycenter vs. Simple Average) is a direct comparison of two aggregation strategies explicitly mentioned, making it a very focused and informative ablation. The second ablation (NTK transformation vs. simpler GP) tests the core mechanism of the implicit functional transformation. I will rank the Barycenter ablation slightly higher due to its direct comparison of two discussed aggregation methods.

The metrics to report should align with those used in the paper's experimental evaluation: RMSE and NLL for regression tasks, Accuracy and OOD-AUC for classification tasks, and Cumulative Regret for the contextual bandit task.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### ifBDE Barycenter Ablation
- **Ablated Part**: Wasserstein Barycenter aggregation for ensemble GPs in ifBDE
- **Action**: REPLACE
- **Replacement**: 
  - Simple average of GP means and covariances (as in Eq 19)
- **Metrics**: RMSE, NLL, Accuracy, OOD-AUC, Cumulative Regret

### ifBNN GP Transformation Ablation
- **Ablated Part**: NTK-based GP transformation of the BNN posterior in ifBNN
- **Action**: REPLACE
- **Replacement**: 
  - Simpler Gaussian approximation on measurement set (e.g., N(mean, learned diagonal covariance))
- **Metrics**: RMSE, NLL, Accuracy, OOD-AUC, Cumulative Regret

</div>