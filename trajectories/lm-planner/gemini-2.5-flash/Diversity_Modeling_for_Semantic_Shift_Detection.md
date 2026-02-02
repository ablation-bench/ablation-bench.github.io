<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Diversity_Modeling_for_Semantic_Shift_Detection

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Diversity Modeling for Semantic Shift Detection" proposes Bi-directional Regularized Diversity Modulation (BiRDM), which includes several key components: bi-directional diversity modulation (ψ⁻, ψ⁺), Smoothness Regularization (SmoReg) with a projection matrix P and sampling, Batch Normalization Simulation (BNSim) utilizing auxiliary data, and a modulation constraint (Lmod). The method aims to model non-semantic diversity while suppressing generalization to semantic shifts.

The paper includes several ablation studies in Section 4.3 and Appendix C. These cover the contribution of individual components (ψ⁺, ψ⁻, Lmod, Lsmo, P, BNSim) in Table 2(a), the effect of bi-directional modulation (Table 2b, Figure 7), memory quantity (Table 2c, Figure 11), sampling quantity and strategy (Table 2d, 2e), number of modulation stages (Table 3), the weight γ for Lmod (Table 4), and model architecture (Table 6).

Based on the method description and the existing ablations, two important aspects are not fully explored:

1.  **The specific role of auxiliary data within BNSim:** BNSim is trained with both ID data (simulating BN output) and auxiliary data (optimizing reconstruction). The paper states that auxiliary data helps push potential OODs away. While the overall contribution of BNSim is shown (Table 2a), an ablation specifically removing the auxiliary data training objective would clarify its unique contribution to OOD discriminability, separate from BNSim's role in tracking BN for IDs.
2.  **The contribution of each term in the final scoring function:** The final OOD score S is a weighted sum of four different terms derived from the model's outputs (reconstruction error, BNSim distance, SmoReg projection distance, modulation magnitude). The paper provides intuition for these terms and mentions hyperparameters α1, α2, α3, but there is no ablation study showing the effect of using different combinations of these terms or varying their weights. This makes it difficult to assess the relative importance of each component's output in the final detection decision.

Therefore, I propose two missing ablation studies focusing on these aspects. The first is to remove the auxiliary data training objective from BNSim to isolate its effect. The second is to evaluate the performance using different combinations of the terms in the final scoring function to understand their individual and combined contributions. Both ablations should use AUC as the primary metric, consistent with the paper's evaluation.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablate BNSim Auxiliary Data
- **Ablated Part**: Training objective of BNSim using auxiliary data (first term in Lsim)
- **Action**: REMOVE
- **Metrics**: AUC

### Ablate Scoring Function Terms
- **Ablated Part**: Terms included in the final OOD scoring function S
- **Action**: REPLACE
- **Replacement**: 
  - Term 1 only (Reconstruction Error)
  - Term 2 only (BNSim distance)
  - Term 3 only (SmoReg projection distance)
  - Term 4 only (Modulation magnitude)
  - Term 1 + Term 2
  - Term 1 + Term 3
  - Term 1 + Term 4
  - Term 1 + Term 2 + Term 3 + Term 4 (Full model)
- **Metrics**: AUC

</div>