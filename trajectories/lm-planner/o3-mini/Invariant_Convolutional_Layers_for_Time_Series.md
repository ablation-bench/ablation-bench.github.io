<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Invariant_Convolutional_Layers_for_Time_Series

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two missing ablation studies that target key design choices not yet fully explored in the paper. The first study focuses on the design decision to mix invariant and standard (variant) convolution filters in the same embedding layer. Although the authors provide ablations where only one type of filter is used (INVCONVNET-N, INVCONVNET-O, INVCONVNET-T), the overall InvConvNet architecture uses a fixed, equal (or pre‐defined) split of filters between invariant (both offset and trend invariant) and standard ones. Varying this proportion would help determine the sensitivity of the method’s performance (on classification accuracy, anomaly detection F1-score, and reconstruction error) to the degree of enforced invariance, thereby better understanding the trade-off between learning invariant representations and preserving raw signal nuances.

The second ablation we propose concerns the normalization step applied in the invariant embedding (see Proposition 2 and Equation (3)). The current design normalizes the projected signal L(m) to form an invariant representation. Studying what happens if this normalization is removed (i.e. using L(m) directly) would provide insights into whether the amplitude information lost by normalization is critical, or if the normalization indeed enhances the invariance needed for the targeted deformations. This experiment would report similar metrics to assess its impact on overall performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Invariant vs Variant Filter Ratio Ablation
- **Ablated Part**: The ratio of invariant (offset and trend invariant) convolutional filters to standard convolutional filters in the combined embedding layer of InvConvNet
- **Action**: REPLACE
- **Replacement**: 
  - Equal split (current design)
  - 60% invariant + 40% standard
  - 40% invariant + 60% standard
- **Metrics**: classification accuracy, anomaly detection F1-score, reconstruction error

### Normalization Ablation in Invariant Embedding
- **Ablated Part**: The normalization of the invariant embedding output (i.e., mapping L(m) to L(m)/||L(m)||), which is used to enforce amplitude invariance
- **Action**: REPLACE
- **Replacement**: 
  - With normalization (current design)
  - Without normalization (using L(m) directly)
- **Metrics**: classification accuracy, anomaly detection F1-score, reconstruction error

</div>