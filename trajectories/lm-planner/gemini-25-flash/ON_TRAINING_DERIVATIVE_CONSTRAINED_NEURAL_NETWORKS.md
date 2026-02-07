<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/ON_TRAINING_DERIVATIVE_CONSTRAINED_NEURAL_NETWORKS

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "ON TRAINING DERIVATIVE-CONSTRAINED NEURAL NETWORKS" proposes three main techniques to improve training of neural networks with derivative constraints (DC NNs): the Integrated ReLU (IReLU) activation function, denormalization (removing normalization layers), and label rescaling. The authors demonstrate that the combination of these methods improves performance on quantum chemistry and PINN tasks.

The paper includes some ablation studies in Appendix C. Appendix C.1 investigates the IReLU activation, showing that IReLU alone can be unstable (Table 7) but is beneficial when combined with denormalization and label rescaling (Table 8). Appendix C.2 investigates denormalization and label rescaling together, comparing original models (with normalization) to denormalized models with label rescaling (Table 9). This shows the combined effect of the two stabilization techniques using original activations.

While these ablations show the benefit of the proposed combination and the necessity of the stabilization techniques for IReLU, they do not fully disentangle the individual contributions of denormalization and label rescaling. Specifically:
1.  The effect of removing normalization layers (denormalization) *alone*, without applying label rescaling or IReLU, is not shown. This would directly test the authors' hypothesis that DC training is sensitive to units and that unit-insensitive normalization layers are detrimental. Comparing a standard model (with normalization and original activation) to the same model with normalization layers removed (but still using the original activation and no label rescaling) would isolate the impact of denormalization.
2.  The individual effect of label rescaling is not isolated. Table 9 compares original models (with normalization) to denormalized models *with* label rescaling. It does not compare denormalized models *without* label rescaling to denormalized models *with* label rescaling (both using original activations). This comparison would clarify the specific contribution of label rescaling as a stabilization technique when normalization layers are absent.

Therefore, I propose two missing ablation studies to address these points and provide a clearer understanding of the roles of denormalization and label rescaling. The first ablation focuses on the impact of removing normalization layers, and the second isolates the effect of label rescaling within a denormalized setting. These are ranked by their importance in validating the core hypotheses about stabilization in DC training.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Denormalization Ablation (Baseline)
- **Ablated Part**: Normalization layers in the original network architectures
- **Action**: REMOVE
- **Metrics**: Energy Loss (kcal/mol), Force Loss (kcal/mol/A), Energy MAE Loss (eV), Force MAE Loss (eV/A), MSE, Lf, LIC, LBC, LICp, LICd, LICv, LBCp, LBCd, LBCv, LICu, LBCu, LBCv

### Label Rescaling Ablation (Denormalized)
- **Ablated Part**: Label Rescaling procedure
- **Action**: REMOVE
- **Metrics**: Energy Loss (kcal/mol), Force Loss (kcal/mol/A), Energy MAE Loss (eV), Force MAE Loss (eV/A), MSE, Lf, LIC, LBC, LICp, LICd, LICv, LBCp, LBCd, LBCv, LICu, LBCu, LBCv

</div>