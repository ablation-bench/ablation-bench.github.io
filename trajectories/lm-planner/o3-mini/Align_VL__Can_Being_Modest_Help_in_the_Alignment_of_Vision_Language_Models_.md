<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Align_VL__Can_Being_Modest_Help_in_the_Alignment_of_Vision_Language_Models_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on a close review of the paper and its ablation section, the key components of the proposed Align-VL method include the Random Perturbation (RP) and Embedding Smoothing (ES) mechanisms that are shown to boost performance in image‐text retrieval tasks. However, while the paper ablates the effect of applying these components (i.e. the inclusion versus exclusion of RP and ES), two important facets have not been explored in a dedicated ablation study. 

First, although RP is applied before the V-L adapters in the current formulation, it is unclear whether the order in which Gaussian noise is injected influences performance. In other words, applying noise before versus after projection through the adapter could affect how the noise propagates and interacts with the learnt parameters — potentially impacting feature robustness and generalization. Investigating this alternative order is essential to understand the sensitivity of the method to the position of noise injection in the pipeline.

Second, the paper reports the use of a fixed noise level (σ = 0.01) during training but does not explore how varying this magnitude might affect model performance. A sensitivity analysis on σ, testing values from no noise up to larger perturbation levels, would be valuable. This study would emphasize the trade-off between injecting sufficient uncertainty and preserving feature quality.

Both studies use retrieval accuracy metrics (R@1, R@5, and R@10) similar to those in the paper’s experiments. The proposed experiments can therefore provide further insights into design choices that directly influence the method’s effectiveness.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A: Noise Injection Order
- **Ablated Part**: The position of applying Gaussian noise in the pipeline (before vs. after the V-L adapter projection)
- **Action**: REPLACE
- **Replacement**: 
  - Apply noise before V-L adapter (current approach)
  - Apply noise after V-L adapter
- **Metrics**: R@1, R@5, R@10

### Ablation B: Noise Magnitude Sensitivity
- **Ablated Part**: The magnitude (σ) of the Gaussian noise used in random perturbation
- **Action**: REPLACE
- **Replacement**: 
  - 0 (no noise)
  - 0.005
  - 0.01
  - 0.02
- **Metrics**: R@1, R@5, R@10

</div>