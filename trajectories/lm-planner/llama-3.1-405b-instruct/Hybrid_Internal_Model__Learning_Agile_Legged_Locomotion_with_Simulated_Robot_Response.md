<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Hybrid_Internal_Model__Learning_Agile_Legged_Locomotion_with_Simulated_Robot_Response

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents a novel approach to legged locomotion control, called Hybrid Internal Model (HIM), which combines the benefits of model-based control and learning-based methods. The authors propose two ablation studies to evaluate the effectiveness of their approach.

The first ablation study investigates the impact of removing the internal model from the HIM framework. This study aims to understand the contribution of the internal model to the overall performance of the system. By removing the internal model, the authors can assess whether the policy network alone is sufficient to achieve robust locomotion control.

The second ablation study examines the effect of replacing the contrastive learning objective with a regression-based objective. This study aims to evaluate the importance of using contrastive learning in the HIM framework. By comparing the performance of the system with and without contrastive learning, the authors can determine whether this component is crucial for achieving robust and agile locomotion.

Both ablation studies provide valuable insights into the HIM framework and its components. By analyzing the results of these studies, the authors can refine their approach and identify areas for further improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Internal Model
- **Action**: REMOVE
- **Metrics**: Normalized Linear Velocity Tracking Score, Normalized Angular Velocity Tracking Score, Maximum Reachable Terrain Level

### Ablation Study 2
- **Ablated Part**: Contrastive Learning Objective
- **Action**: REPLACE
- **Replacement**: 
  - Regression-based Objective
- **Metrics**: Normalized Linear Velocity Tracking Score, Normalized Angular Velocity Tracking Score, Maximum Reachable Terrain Level

</div>