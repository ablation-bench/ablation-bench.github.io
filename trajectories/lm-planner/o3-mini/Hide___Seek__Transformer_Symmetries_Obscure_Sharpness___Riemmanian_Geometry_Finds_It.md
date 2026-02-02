<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Hide___Seek__Transformer_Symmetries_Obscure_Sharpness___Riemmanian_Geometry_Finds_It

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Two missing ablation experiments emerge from our review of the paper. First, although the paper thoroughly investigates the contributions of the norm correction and second‐order weight corrections in the geodesic sharpness measure (with ablations reported on MNLI using BERT), the sensitivity of geodesic sharpness to the choice of the radius ρ used to define the geodesic ball is not studied. The value of ρ directly governs the “neighborhood” around a trained model from which loss variations are measured, and its selection may critically influence the correlation with generalization gap. An ablation study that systematically varies ρ over a range of candidate values (for example, 1e-3, 1e-2, 1e-1) would quantify the robustness of the measure with respect to this hyperparameter. 

Second, while the paper includes ablations for the removal of the norm correction and the second order adjustments on a BERT/MNLI setup (using metric [15] and [34]), it would be valuable to verify the consistency of these contributions across different model domains. In particular, conducting the same ablations–removing either the norm correction part or the second-order weight corrections–on Vision Transformers (e.g. on the ImageNet dataset) could clarify whether the observed improvements in prediction of the generalization gap are consistent across modalities (NLP vs. vision). This cross-domain consistency study is important given the paper’s focus on transformers in both language and vision.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Varying Geodesic Ball Radius
- **Ablated Part**: The hyper-parameter ρ determining the radius of the geodesic ball used in approximating geodesic sharpness
- **Action**: REPLACE
- **Replacement**: 
  - 1e-3
  - 1e-2
  - 1e-1
- **Metrics**: Kendall tau correlation, Generalization gap

### Ablation: Cross-Domain Consistency of Geodesic Sharpness Components
- **Ablated Part**: The symmetry-correcting components (norm correction and second-order weight update corrections) in geodesic sharpness as applied in transformer attention layers
- **Action**: REMOVE
- **Metrics**: Kendall tau correlation, Generalization gap

</div>