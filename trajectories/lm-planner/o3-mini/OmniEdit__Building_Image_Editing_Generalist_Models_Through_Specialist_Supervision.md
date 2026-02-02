<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/OmniEdit__Building_Image_Editing_Generalist_Models_Through_Specialist_Supervision

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One major contribution of OmniEdit is the use of specialist-to-generalist supervision by leveraging multiple specialist models; however, the paper does not explore how critical this multi-specialist supervision is. An ablation study replacing multi-specialist supervision with a single generic supervision signal would help isolate the contribution of diverse specialist signals. Another important aspect is the use of training data with diverse aspect ratios to handle real-world images. The paper claims that incorporating multi-aspect ratio images improves performance, yet it does not evaluate what happens if training is restricted to a fixed (e.g., 1:1) aspect ratio. Evaluating this would validate the importance of diverse aspect ratio training on generalization.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Specialist Supervision
- **Ablated Part**: The specialist-to-generalist supervision mechanism that leverages multiple task-specific specialist models
- **Action**: REPLACE
- **Replacement**: 
  - Single generic specialist
  - Uniform supervision without task-specific differentiation
- **Metrics**: VIEScore (PQ, SC, Overall), Human Evaluation (PQ, SC, Accuracy)

### Ablation on Aspect Ratio Diversity
- **Ablated Part**: The multi-aspect ratio training data strategy
- **Action**: REPLACE
- **Replacement**: 
  - Fixed 1:1 aspect ratio training
- **Metrics**: VIEScore (PQ, SC, Overall), Human Evaluation (PQ, SC, Accuracy), Edit consistency across aspect ratios

</div>