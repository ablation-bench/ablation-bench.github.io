<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Invariant_Convolutional_Layers_for_Time_Series

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Invariant Convolutional Layers for Time Series" proposes INVCONVNET, a neural network architecture featuring novel invariant convolutional layers designed to capture time series patterns robust to deformations like offset shifts, scaling, and linear trends. The core of the method lies in an embedding layer that combines standard (variant) convolutions with two types of invariant convolutions: one invariant to offset shift and scaling, and another invariant to linear trend and scaling. This combination is referred to as a "pool of convolutions". The paper evaluates INVCONVNET on classification and anomaly detection tasks, demonstrating superior performance against several baselines.

The paper includes several ablation studies:
1.  **Contribution of Kernel Types (Table 2):** This study compares the full INVCONVNET (using a mix of standard, offset-invariant, and linear-trend-invariant kernels) against variants that use *only* one type of kernel (INVCONVNET-N, INVCONVNET-O, INVCONVNET-T). This effectively ablates the *presence* of each kernel type but keeps the total number of kernels constant and the proportion of each type in the full model fixed (stated as "identical" or "almost equal contribution" in the appendix).
2.  **Robustness under Synthetic Deformations (Table 3):** This experiment reinforces the findings of Table 2 by showing how the different kernel types perform under specific synthetic deformations, highlighting the robustness conferred by the invariant kernels.
3.  **Transfer Learning (Table 4):** Compares the full INVCONVNET and INVCONVNET-N (only normal kernels) in a transfer learning setting, showing the benefit of invariant kernels for generalization.
4.  **Anomaly Detection Reconstruction (Table 11 in Appendix):** Compares INVCONVNET's anomaly detection performance against standard CNNs, suggesting the benefit comes from both the invariant embedding and the use of decomposition coefficients in reconstruction.

Based on this analysis, two important missing ablation studies are identified:

1.  **Varying the Proportion of Kernel Types:** The existing ablation (Table 2) shows that the *combination* of kernel types is better than using any single type alone. However, it doesn't explore whether the *specific ratio* of standard vs. invariant kernels (or the ratio among the three types) used in the full INVCONVNET is optimal. The paper mentions using "identical" or "almost equal" proportions. An ablation varying these proportions would reveal the sensitivity of the model's performance to the mix of variant and invariant feature extraction and potentially identify an optimal balance. This is a crucial aspect of the proposed "pool of convolutions" design.

2.  **Ablating the Decomposition Coefficients in Anomaly Detection:** For the anomaly detection task, the reconstruction module specifically incorporates the coefficients from the signal decomposition on the invariant basis (Figure 5, Appendix A.2.2). The paper suggests this contributes to performance (Table 11 discussion). A direct ablation study removing the step of combining these coefficients with the linearly projected embedding would isolate their specific contribution to the reconstruction quality and subsequent anomaly detection performance.

These two ablations are ranked by importance. The first ablation (varying kernel proportions) is arguably more fundamental as it directly investigates the composition of the core proposed layer type, relevant to both tasks. The second ablation is specific to the anomaly detection task's reconstruction mechanism.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Kernel Type Proportion
- **Ablated Part**: Ratio of standard, offset-invariant, and linear-trend-invariant kernels in the embedding layer's pool of convolutions.
- **Action**: REPLACE
- **Replacement**: 
  - (High Standard, Low Invariant)
  - (Balanced - similar to paper)
  - (Low Standard, High Invariant)
  - (Varying ratio between Offset and Trend invariant)
- **Metrics**: Accuracy (%), F1-score (%)

### Reconstruction Coefficient Contribution
- **Ablated Part**: Combination of invariant decomposition coefficients with the linearly projected embedding in the anomaly detection reconstruction module.
- **Action**: REMOVE
- **Metrics**: F1-score (%)

</div>