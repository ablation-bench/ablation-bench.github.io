<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Multi_Granularity_Semantic_Revision_for_Large_Language_Model_Distillation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Multi-Granularity Semantic Revision for Large Language Model Distillation" proposes a novel knowledge distillation method for LLMs that operates at three levels: sequence, token, and span. The method combines a Sequence Correction and Re-generation (SCRG) strategy, a Distribution Adaptive Clipping Kullback-Leibler (DAC-KL) loss, and a Span-level Correlation Consistency loss. The overall objective function is a simple sum of the Supervised Fine-Tuning (SFT) loss, the DAC-KLD loss, and the Span loss (LSFT + LDAC-KLD + Lspan).

The paper includes several ablation studies in Section 5.3 and Appendices C, D, and E. These ablations investigate:
1.  The incremental contribution of SCRG, DAC-KL, and Span loss (Table 2).
2.  The effectiveness of SCRG compared to different student-generation methods (Table 3a).
3.  The effectiveness of DAC-KL compared to other distillation loss functions (Table 3c) and different components within DAC-KL (Table 3b, Appendix D.1 Table 7).
4.  The impact of SCRG frequency (Table 4c, Appendix E.3 Table 10).
5.  The Span-level loss compared to alternative relation calculations (Appendix C Table 5).

While these ablations cover the individual components and some variations, there are a couple of important aspects that are not fully explored through ablation:

1.  **Weights of the Loss Components:** The overall loss is a sum of three terms. The paper uses a simple sum (implicitly weight 1 for each term, although LSFT is often treated separately in practice). A standard and crucial ablation is to investigate the relative importance of the non-SFT loss terms (LDAC-KLD and Lspan) by varying their weights. This helps understand if one loss is more critical than the other or if a specific balance is required. The current ablations only show the effect of adding these terms with a fixed weight (presumably 1) on top of SFT (and SCRG). Testing different coefficients for LDAC-KLD and Lspan relative to LSFT would provide valuable insight into the optimal combination and the sensitivity of the method to these weights.

2.  **Adaptive Nature of DAC-KL:** The DAC-KL loss is designed to be "distribution adaptive" by using a learnable sub-network to predict clipping quantiles. While Appendix D.1 compares DAC-KL to a "Fixed clipping threshold", this doesn't directly ablate the *learnable* aspect *within* the DAC-KL framework. An important ablation would be to replace the learnable sub-network with a non-learnable, fixed method for determining the clipping region (e.g., using fixed percentiles of the teacher's distribution) and compare its performance to the learnable version. This would directly validate the necessity and benefit of the adaptive, learnable component.

Based on their importance for understanding the method's performance drivers, varying the loss weights and ablating the learnable part of DAC-KL are the most significant missing ablations. Varying loss weights is arguably more fundamental to the overall objective function design.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Loss Function Weights
- **Ablated Part**: Weights of the DAC-KLD and Span-level Correlation Consistency loss components in the overall objective function
- **Action**: REPLACE
- **Replacement**: 
  - {'dac_weight': 1.0, 'span_weight': 0.0}
  - {'dac_weight': 0.0, 'span_weight': 1.0}
  - {'dac_weight': 0.5, 'span_weight': 0.5}
  - {'dac_weight': 1.0, 'span_weight': 0.5}
  - {'dac_weight': 0.5, 'span_weight': 1.0}
  - {'dac_weight': 1.0, 'span_weight': 1.0}
- **Metrics**: Dolly Evaluation, Self-Instruct, Vicuna, Super-Natural, Unnatural, Average

### DAC-KL Fixed Clipping
- **Ablated Part**: Learnable sub-network for predicting clipping quantiles (u, l) in DAC-KL loss
- **Action**: REPLACE
- **Replacement**: 
  - Fixed quantiles (e.g., top 95% / bottom 5%) based on teacher distribution
  - Fixed percentile thresholds (e.g., 90th and 10th percentile)
- **Metrics**: Dolly Evaluation, Self-Instruct, Vicuna, Super-Natural, Unnatural, Average

</div>