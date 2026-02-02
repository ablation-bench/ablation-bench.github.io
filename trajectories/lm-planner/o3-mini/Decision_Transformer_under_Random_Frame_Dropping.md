<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Decision_Transformer_under_Random_Frame_Dropping

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The first missing ablation we propose is to evaluate the model’s robustness to corrupted observations. In the current work, dropped frames are simply replaced with the last observed frame along with adding a drop‐span embedding. However, in many practical applications, sensor failures or communication issues may result not only in missing data but also in corrupted observations (e.g., blurred or noisy images). An ablation study that replaces dropped frames with various types of corrupted observations—even when still providing the drop-span information—would provide deeper insight into whether the robustness granted by the explicit drop-span embedding extends to more realistic degradation in the data quality. The evaluation can be done by replacing the “last observation” filler with a corrupted version (using, for example, Gaussian blur, Gaussian noise, or salt-and-pepper noise) and measuring how the average return changes under different corruption intensities.

The second missing ablation is to explore alternative designs for the drop-span encoding module. Currently, a learned drop-span encoder is used to explicitly inject the information about the number of dropped frames into the token embeddings. Although the paper already shows the benefit of an explicit drop-span embedding over an implicit method, it does not evaluate whether other encoding schemes (e.g., fixed sinusoidal positional encoding, non-learnable fixed embeddings) could yield similar or even improved performance. This ablation would help determine if the benefit arises purely from the availability of drop-span information or if the learning of a dedicated embedding is crucial.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Observation Corruption Robustness
- **Ablated Part**: Frame replacement strategy for dropped observations; instead of repeating the last observation, corrupted observations (e.g., blurred/noisy) are inserted
- **Action**: REPLACE
- **Replacement**: 
  - Gaussian blur
  - Gaussian noise
  - Salt-and-pepper noise
- **Metrics**: Average Return, Performance under varying corruption intensities

### Alternative Drop-Span Encoding Methods
- **Ablated Part**: Design of the drop-span embedding module
- **Action**: REPLACE
- **Replacement**: 
  - Sinusoidal positional encoding
  - Non-learnable fixed embedding
- **Metrics**: Average Return, Robustness under high drop rates

</div>