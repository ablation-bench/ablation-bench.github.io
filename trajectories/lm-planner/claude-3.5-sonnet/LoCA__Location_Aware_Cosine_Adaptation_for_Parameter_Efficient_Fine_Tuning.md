<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/LoCA__Location_Aware_Cosine_Adaptation_for_Parameter_Efficient_Fine_Tuning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the abstract, LoCA appears to be a frequency-domain parameter-efficient fine-tuning method that uses:
1. Inverse Discrete Cosine Transform (iDCT) instead of traditional low-rank decomposition
2. Selective locations of learnable components
3. Finite-difference approximation for gradient estimation
4. Dynamic selection of frequency components during training

The two most critical components that would warrant ablation studies (assuming they're not already covered in the paper) would be:
1. The dynamic selection mechanism of frequency components
2. The location-awareness aspect through selective locations of learnable components

These components seem central to the method's novelty and claimed improvements over LoRA.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Dynamic Selection Ablation
- **Ablated Part**: Dynamic selection mechanism of frequency components
- **Action**: REPLACE
- **Replacement**: 
  - random selection
  - fixed predetermined selection
- **Metrics**: parameter efficiency, task performance, computational cost

### Location Awareness Ablation
- **Ablated Part**: Selective locations of learnable components
- **Action**: REPLACE
- **Replacement**: 
  - uniform distribution
  - random locations
- **Metrics**: parameter efficiency, task performance

</div>