<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Prototypical_evoluation_for_few_shot_learning_in_vision_language_model_adaptation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces two key components: (1) the use of off‐the‐shelf image centroids to form class prototypes and (2) the integration of learnable shift vectors to dynamically calibrate these prototypes. Although the experiments vary the calibration strength (α) and compare to several baselines, the impact of these design choices in isolation is not fully explored. One important missing ablation is to remove the learnable shift vectors entirely to assess how much the dynamic prototype evolution contributes to few-shot performance and out-of-distribution (OOD) generalization. Another complementary ablation is to study the prototype aggregation strategy. The current method uses a mean (centroid) aggregation; testing alternatives such as median or weighted aggregation could provide further insight into the robustness of the prototype estimation. These ablations would help isolate and quantify the contributions of the dynamic calibration and the aggregation strategy to the overall method’s performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Shift Vectors Removal
- **Ablated Part**: Learnable shift vectors that dynamically calibrate class prototypes
- **Action**: REMOVE
- **Metrics**: few-shot accuracy, OOD accuracy

### Ablation on Prototype Aggregation Method
- **Ablated Part**: The prototype aggregation strategy used to compute class centroids from support images
- **Action**: REPLACE
- **Replacement**: 
  - mean aggregation
  - median aggregation
  - weighted average aggregation
- **Metrics**: few-shot accuracy, OOD accuracy

</div>