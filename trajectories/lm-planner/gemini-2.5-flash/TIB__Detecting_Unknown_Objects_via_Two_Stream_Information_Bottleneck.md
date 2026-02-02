<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/TIB__Detecting_Unknown_Objects_via_Two_Stream_Information_Bottleneck

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "TIB: Detecting Unknown Objects via Two-Stream Information Bottleneck" proposes a method for unsupervised out-of-distribution object detection using a Two-Stream Information Bottleneck (TIB). The method consists of a standard Information Bottleneck (IB) branch to extract task-relevant (ID object) features and a Reverse Information Bottleneck (RIB) branch to generate simulative OOD features. These two streams are trained jointly using several loss functions, including L_IB (for the IB branch, including KL divergence terms and standard detection losses), L_dis (maximizing prediction discrepancy between the two streams), and L_uncertainty (an energy-based loss to distinguish ID from simulative OOD features). The IB branch also incorporates a Mixture of Information Bottlenecks (MIB) module to further enhance object-related information from RoI features.

The paper includes several ablation studies:
1.  Analysis of IB and RIB (Table 4): Compares the full TIB model against variants using only the IB branch (trained with VOS synthesis) or only the RIB branch. This shows the overall contribution of each main stream.
2.  Analysis of the branch number in MIB (Table 5): Investigates the impact of varying the number of branches in the MIB module.
3.  Analysis of hyper-parameters (Appendix A.3): Studies the effect of different values for β, λ, and τ.
4.  Further Analysis about RIB (Appendix A.4): Explores adding a mutual information constraint for RIB and replacing the variational operation with convolution in RIB.
5.  Ablation studies about Equation 4 (Appendix A.8): Evaluates the gating mechanism vs mean for MIB aggregation and learned vs fixed weight for the residual connection in MIB.

Based on the method description and existing ablations, I identify two important missing ablation studies:

1.  **Ablation of the MIB Module:** The MIB module is a specific architectural design within the IB stream intended to enhance object-related information from RoI features. While the paper ablates the *configuration* of MIB (number of branches, aggregation, residual weight), it does not show the performance impact of removing the *entire module*. An ablation study comparing the full TIB model against a version where the MIB is removed (i.e., using the raw RoI features directly) would demonstrate the overall contribution of this complex module.

2.  **Ablation of Interaction Losses (L_dis and L_uncertainty):** The core idea of TIB is the interaction between the IB and RIB streams, facilitated by the L_dis and L_uncertainty losses. L_dis pushes the RIB features away from the IB predictions, generating simulative OOD features. L_uncertainty explicitly trains the model to assign low energy scores to ID features and high energy scores to simulative OOD features, which is directly used for OOD detection inference. While hyperparameter tuning for λ and τ is shown, removing these losses entirely would reveal whether the explicit objectives they enforce are crucial for the performance gains, or if the separate IB and RIB objectives alone (without explicit interaction/discrimination training via these losses) are sufficient. This tests a fundamental aspect of the TIB training strategy for OOD discrimination.

Both of these ablations are crucial for understanding the contribution of key components and the training strategy of TIB. I will suggest these two as the most important missing ablations. The metrics used in the paper for OOD-OD evaluation are FPR95, AUROC, and mAP (ID), which should be used for these ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of MIB Module
- **Ablated Part**: Mixture of Information Bottlenecks (MIB) module for enhancing RoI features
- **Action**: REMOVE
- **Metrics**: FPR95, AUROC, mAP (ID)

### Ablation of Interaction Losses
- **Ablated Part**: Prediction discrepancy loss (L_dis) and Uncertainty loss (L_uncertainty)
- **Action**: REMOVE
- **Metrics**: FPR95, AUROC, mAP (ID)

</div>