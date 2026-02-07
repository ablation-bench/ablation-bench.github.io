<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Privacy_Preserving_Vision_Transformer_on_Permutation_Encrypted_Images

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that the authors have conducted several ablation studies, including:
1. Impact of RPE (Reference-based Positional Embedding) on classification performance
2. Impact of patch size on object detection performance 
3. Impact of nonlinear embedding on object detection performance

However, there are two critical missing ablation studies that would help better understand the method's key components:

1. The most important missing ablation is studying the impact of sub-patch count in the MI (Mixing-up) encryption strategy. The authors fix it to 4 sub-patches per patch without justifying this choice. Testing different numbers of sub-patches would help understand how this parameter affects both privacy preservation and model performance.

2. Another important missing ablation is investigating different mixing functions for the MI strategy. The authors use simple averaging (1/M sum) to mix sub-patches, but don't explore alternatives. Testing different mixing functions could reveal if there are better options for balancing privacy and performance.

These ablations would provide crucial insights into the key design choices of their encryption strategies.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Sub-patch Count Ablation
- **Ablated Part**: Number of sub-patches M in the MI encryption strategy
- **Action**: REPLACE
- **Replacement**: 
  - 2
  - 4
  - 8
  - 16
- **Metrics**: AP, Privacy Leakage Ratio

### Mixing Function Ablation
- **Ablated Part**: Mixing function in MI encryption strategy
- **Action**: REPLACE
- **Replacement**: 
  - average
  - weighted sum
  - max pooling
  - learned mixing
- **Metrics**: AP, Privacy Leakage Ratio

</div>