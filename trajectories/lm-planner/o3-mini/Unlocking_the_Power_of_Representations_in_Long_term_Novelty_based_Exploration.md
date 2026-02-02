<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Unlocking_the_Power_of_Representations_in_Long_term_Novelty_based_Exploration

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two additional ablations that seem missing from the paper. First, although RECODE’s memory update rule carefully adjusts cluster centers using a convex combination update (Eq. 4), the benefit of this online update compared to keeping the atom fixed (i.e. only updating the count) has not been isolated. An ablation study that removes the online center update—by leaving the cluster center fixed and only incrementing its count when a new embedding falls in its neighborhood—would test whether the adaptive shift in atom positions is essential to track non-stationarities and improve exploration. Key performance metrics would include Human Normalized Scores (HNS) and area under the learning curve (AUC) on both Atari and DM-HARD-8, as these are the metrics used in the paper.

Second, while the authors introduce an adaptive bandwidth mechanism via an exponential moving average (EMA) using parameter τ to update the dema parameter, there is no ablation that evaluates its exact contribution. Replacing the EMA with a fixed bandwidth or a different update strategy (such as using a simple moving average with various window lengths) would reveal how sensitive the overall performance is to the adaptive adjustment of distances used in the density kernel. The same metrics (HNS, average return, learning stability) can quantify any degradation or improvement in exploration quality.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Fixed Cluster Center Update Ablation
- **Ablated Part**: Online memory update rule: using the adaptive convex combination update (Eq. 4) for updating cluster centers
- **Action**: REPLACE
- **Replacement**: 
  - Do not update the atom's position (keep it fixed) and only increment the count when an embedding is assigned
- **Metrics**: Human Normalized Score, AUC of episode returns

### Adaptive Bandwidth EMA Ablation
- **Ablated Part**: Adaptive bandwidth mechanism for updating d2_ema using the exponential moving average
- **Action**: REPLACE
- **Replacement**: 
  - Use a fixed d2_ema value
  - Use a simple moving average with different window sizes
- **Metrics**: Human Normalized Score, Average Episode Return, Stability of exploration bonus

</div>