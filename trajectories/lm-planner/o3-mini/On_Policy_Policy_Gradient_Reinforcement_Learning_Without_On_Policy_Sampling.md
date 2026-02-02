<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/On_Policy_Policy_Gradient_Reinforcement_Learning_Without_On_Policy_Sampling

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Our analysis identified two key design choices that, although integral to PROPS, were not isolated in the experimental evaluation. First, the PROPS update applies a uniform correction to all under‐sampled actions irrespective of their estimated advantage. This might be inefficient, as actions with negligible advantage may not need aggressive correction while those with high advantage might benefit from a larger update. An ablation that introduces advantage-based weighting into the behavior policy update could reveal whether selective correction improves data efficiency and reduces sampling error. Second, PROPS resets the behavior policy to the target policy at every update before applying local adjustments. This reinitialization may limit the benefits of accumulating corrections over time. Investigating an alternative “warm‐start” approach where the behavior policy is not reinitialized (thus allowing a continuous evolution) could provide insights into trade‐offs between stability and rapid data distribution correction. These proposed ablations are ranked by importance, with the advantage‐weighted update being the primary one.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Advantage-Based Weighted Behavior Update
- **Ablated Part**: The current PROPS update uniformly adjusts action probabilities without considering the associated advantage values.
- **Action**: REPLACE
- **Replacement**: 
  - absolute advantage weighting
  - positive-only advantage weighting
  - normalized advantage weighting
- **Metrics**: DKL(π_D || π_θ), IQM return, Data Efficiency

### Behavior Policy Re-initialization Ablation
- **Ablated Part**: The procedure that reinitializes the behavior policy to the target policy at every update, thereby discarding potentially useful cumulative adjustments.
- **Action**: REPLACE
- **Replacement**: 
  - reinitialize to target policy
  - warm-start without reinitialization
- **Metrics**: DKL(π_D || π_θ), IQM return, Training Stability

</div>