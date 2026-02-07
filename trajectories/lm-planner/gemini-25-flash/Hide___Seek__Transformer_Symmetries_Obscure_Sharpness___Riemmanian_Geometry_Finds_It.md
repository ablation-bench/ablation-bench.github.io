<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Hide___Seek__Transformer_Symmetries_Obscure_Sharpness___Riemmanian_Geometry_Finds_It

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Hide & Seek: Transformer Symmetries Obscure Sharpness & Riemmanian Geometry Finds It" proposes a novel sharpness measure, geodesic sharpness, which accounts for transformer symmetries using Riemannian geometry on a quotient manifold. The core idea is to define sharpness based on the loss change within a geodesic ball in this symmetry-corrected parameter space. In practice, they approximate geodesics using a Taylor expansion up to second order and use specific Riemannian metrics for different parts of the network, notably for the GL(h) symmetry in attention layers (Eq. 15 and Eq. 34) and adaptive sharpness (related to GL(1) symmetry and first-order geodesics under a specific metric) for other layers.

The paper includes an ablation study in Appendix G, which investigates the contribution of two components of their geodesic sharpness calculation: the Riemannian norm constraint (referred to as "corrected norm") and the second-order term in the geodesic approximation. This ablation shows that both components contribute to the predictive power, with varying importance depending on the metric used (Metric 15 vs. Metric 34).

Based on my analysis, I've identified two important missing ablation studies:

1.  **Metric Comparison on ImageNet:** The paper proposes two different Riemannian metrics (Eq. 15 and Eq. 34) for the GL(h) symmetry in attention layers. While results for both metrics are shown and compared on the MNLI dataset (Figure 8 vs Figure 10 bottom), only results using Metric 15 are presented for the ImageNet dataset (Figure 4 bottom). A crucial missing ablation is to evaluate Geodesic Sharpness using Metric 34 on the ImageNet dataset and compare its correlation with generalization against Metric 15. This would provide a more complete picture of which metric is more effective across different tasks and potentially reveal if the optimal metric is dataset-dependent.

2.  **Geodesic Scope for Non-Attention Layers:** The paper adopts a mixed approach, applying geodesic sharpness (with the GL(h) metric) to attention layers and adaptive sharpness (related to GL(1) symmetry) to other layers. An ablation is missing to investigate whether applying the full geodesic sharpness framework (using appropriate metrics like Eq. 9 for diagonal networks, which could apply to LayerNorm or biases) to *all* layers with symmetries provides additional benefits compared to the current mixed approach or standard adaptive sharpness applied universally. This would test the broader applicability and necessity of the Riemannian geometry approach beyond the specific GL(h) symmetry in attention.

I will prioritize the Metric Comparison on ImageNet as it directly compares two core technical choices for the primary application (vision transformers on ImageNet) where the method shows strong results. The second ablation on the scope is also important for understanding the method's general applicability but is slightly less critical than validating the choice of metric for the main component (attention).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Metric Comparison (ImageNet)
- **Ablated Part**: Choice of Riemannian metric for attention layers (Eq. 15 vs Eq. 34)
- **Action**: REPLACE
- **Replacement**: 
  - Metric 15 (Eq. 15)
  - Metric 34 (Eq. 34)
- **Metrics**: Kendall rank correlation coefficient (τ) with generalization gap

### Geodesic Scope (Non-Attention Layers)
- **Ablated Part**: Application of adaptive sharpness vs. geodesic sharpness for non-attention layers with symmetries
- **Action**: REPLACE
- **Replacement**: 
  - Current mixed approach (Geodesic for Attention, Adaptive for others)
  - Geodesic for all layers with symmetries
- **Metrics**: Kendall rank correlation coefficient (τ) with generalization gap

</div>