<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/LoCA__Location_Aware_Cosine_Adaptation_for_Parameter_Efficient_Fine_Tuning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The LoCA method introduces two major contributions: (1) a dynamic, location-aware selection of frequency components using finite-difference approximations over the iDCT spectrum and (2) a cosine adaptation mechanism that modulates these frequency components for parameter-efficient fine-tuning. However, the paper does not report ablation studies that isolate these components to determine their individual contributions. One missing ablation is to compare the dynamic (learned and adaptive) frequency selection with a fixed selection of frequency components. By replacing the dynamic mechanism with fixed selection strategies (e.g., fixed low-frequency, fixed uniform, or random fixed positions), we can assess how crucial dynamic selection is for obtaining the superior expressivity and parameter efficiency claimed by LoCA. Additionally, since cosine adaptation is central to the method’s design, another useful ablation would be to remove the cosine adaptation module entirely. This would help determine whether the cosine-based scaling provides a significant improvement over a baseline iDCT-based adaptation without cosine modulation. Both ablations would be evaluated on the same metrics (accuracy, parameter efficiency, and compute cost) as reported in the paper.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Dynamic vs. Fixed Frequency Selection Ablation
- **Ablated Part**: dynamic selection mechanism for learnable frequency components via finite-difference gradient estimation in the DCT spectrum
- **Action**: REPLACE
- **Replacement**: 
  - fixed low-frequency selection
  - fixed uniform selection
  - random fixed selection
- **Metrics**: accuracy, parameter efficiency, compute cost

### Cosine Adaptation Ablation
- **Ablated Part**: cosine adaptation module that scales the learned frequency components in the iDCT domain
- **Action**: REMOVE
- **Metrics**: accuracy, parameter efficiency, compute cost

</div>