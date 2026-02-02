<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Multi_Granularity_Semantic_Revision_for_Large_Language_Model_Distillation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Our review of the paper reveals that the authors carefully ablate the contributions of the multi-granularity components—sequence correction (SCRG), the DAC-KL loss, and the span-level correlation consistency. However, two important experimental variations appear to be missing. First, in the design of the DAC-KL loss, a learnable sub-network is used to adaptively determine the quantile thresholds for clipping the teacher’s probability distribution. Although the paper compares DAC-KL against alternative loss functions and fixed clipping approaches as standalone competitors, it does not explicitly examine the benefit of the learnable adaptive mechanism over a simpler fixed threshold function within the same framework. An ablation study that replaces the learnable sub-network with fixed threshold values (using different fixed lower and upper quantiles) could isolate and quantify the contribution of the adaptive design. Second, the SCRG strategy currently identifies and corrects only the single token with the maximum KL divergence (i.e., the most erroneous token). An alternative strategy would be to use a multi-token correction approach—replacing all tokens that exceed a specified divergence threshold—to study if a more aggressive correction can further reduce generation errors or if excessive correction might hurt performance. Both ablations should be evaluated using the ROUGE-L metric (as in the paper), along with additional measures such as distinct n-gram scores and training efficiency metrics to assess potential tradeoffs.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Adaptive Clipping in DAC-KL
- **Ablated Part**: Learnable sub-network within the DAC-KL loss that adaptively determines quantile thresholds for clipping the teacher's probability distribution.
- **Action**: REPLACE
- **Replacement**: 
  - Fixed threshold (e.g., lower=0.2, upper=0.8)
  - Fixed threshold (e.g., lower=0.3, upper=0.7)
- **Metrics**: ROUGE-L, Exposure Bias, Training Efficiency

### Ablation on Multi-Token Correction in SCRG
- **Ablated Part**: The single-token correction strategy in the SCRG method that only replaces the most erroneous token.
- **Action**: REPLACE
- **Replacement**: 
  - Multi-token correction (replace all tokens whose KL divergence exceeds a fixed threshold, e.g., 0.8)
  - Multi-token correction with adaptive thresholding (e.g., thresholds 0.8, 0.85, 0.9)
- **Metrics**: ROUGE-L, Distinct-n, Training Efficiency

</div>