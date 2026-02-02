<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Policy_Pre_training_for_Autonomous_Driving_via_Self_supervised_Geometric_Modeling

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Our analysis of the paper shows that while several important ablation studies are conducted (e.g., single-stage training, freezing versus joint optimization, and direct PoseNet supervision), two key design choices remain unexamined. First, the method jointly predicts camera intrinsics along with depth and pose in stage one to handle uncalibrated YouTube videos. It is unclear how much this learned intrinsics branch contributes compared to simply using fixed, pre-calibrated intrinsic parameters. An ablation that replaces the learned intrinsics with fixed values would help quantify the importance of this design choice on downstream driving and depth/odometry tasks. Second, the geometric modeling stage relies on using two consecutive frames (adjacent frames with a gap of one) to generate supervision signals via photometric error. Investigating the impact of varying the temporal gap (e.g., using frames that are 2 or 3 steps apart) would reveal how sensitive the method is to the choice of frame interval, potentially affecting the quality of the inferred geometry and subsequent policy pre-training. These experiments would elucidate the contribution of both the intrinsics estimation and the temporal selection strategy to the overall performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Fixed Camera Intrinsics Ablation
- **Ablated Part**: Camera intrinsics estimation module used in stage one of geometric modeling
- **Action**: REPLACE
- **Replacement**: 
  - Fixed calibrated intrinsics
  - Fixed perturbed intrinsics
- **Metrics**: Navigation Success Rate, Driving Score, Depth RMSE, Odometry Abs Rel Error

### Temporal Gap Variation Ablation
- **Ablated Part**: Selection of source frames (temporal gap) in stage one geometric modeling
- **Action**: REPLACE
- **Replacement**: 
  - Adjacent frames (gap=1)
  - Gap=2 frames
  - Gap=3 frames
- **Metrics**: Navigation Success Rate, Driving Score, Open-loop L2 Distance Error

</div>