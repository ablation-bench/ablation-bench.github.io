<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Policy_Pre_training_for_Autonomous_Driving_via_Self_supervised_Geometric_Modeling

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Policy Pre-training for Autonomous Driving via Self-supervised Geometric Modeling" (PPGeo) proposes a two-stage self-supervised framework for pre-training a visual encoder for visuomotor driving tasks. The core idea is to leverage geometric modeling from unlabeled driving videos.

Stage 1 trains a DepthNet and PoseNet using consecutive frames to estimate depth, pose, and intrinsics via photometric error.
Stage 2 trains the visual encoder by predicting ego-motion from a *single* frame, using the frozen DepthNet and intrinsics from Stage 1, also optimized via photometric error. The paper argues that predicting ego-motion from a single frame forces the encoder to learn policy-relevant features.

The paper includes an ablative study (Section 3.6, Table 6) that investigates:
1.  Training Stage 1 and Stage 2 simultaneously (Single stage).
2.  Not freezing DepthNet/Intrinsics in Stage 2.
3.  Using the Stage 1 PoseNet predictions as direct pseudo-label supervision for the Stage 2 visual encoder.

These existing ablations are valuable, confirming the necessity of the two-stage approach, freezing the geometric networks in Stage 2, and the superiority of the dense photometric supervision over sparse pseudo-labels.

However, there are two important aspects of the method that are not ablated, which could further clarify the contribution of specific design choices:

1.  **Input to the Stage 2 Visual Encoder:** The paper highlights that predicting ego-motion from a *single* frame in Stage 2 is crucial for learning policy-related features, contrasting it with Stage 1 which uses consecutive frames. An ablation study is missing to directly compare the performance if the Stage 2 visual encoder *also* took consecutive frames as input (like the Stage 1 PoseNet) instead of just a single frame. This would test the hypothesis that the single-frame input in Stage 2 is indeed essential for learning policy-aware representations, as opposed to just learning general motion estimation from temporal context. This is a fundamental design choice of Stage 2 and its impact should be quantified.

2.  **Specific Loss Components (Minimum Reprojection and Auto-masking):** The loss function relies heavily on techniques borrowed from self-supervised monocular depth estimation, specifically minimum reprojection loss and auto-masking (introduced in Godard et al., 2019). These techniques are designed to handle dynamic objects and occlusions, which are prevalent in driving scenes. While standard for this type of self-supervised task, their specific contribution to the *policy pre-training* objective in PPGeo is not explicitly evaluated. Ablating these components would demonstrate their importance for the robustness and effectiveness of the geometric modeling (Stage 1) and subsequently, the policy pre-training (Stage 2), especially in dynamic environments.

These two missing ablations are important because they probe core design decisions related to the input data structure in the policy learning stage and the specific techniques used to handle challenges in the self-supervised geometric modeling foundation. Evaluating them would provide stronger evidence for the necessity of these choices in achieving the reported performance gains. I will rank the Stage 2 input ablation as slightly more important as it directly relates to the paper's claim about learning policy features from single-frame input.

The relevant metrics for these ablations would be the same downstream task metrics used in the paper's main results and existing ablations, such as Success Rate (for Navigation/Navigation Dynamic), Driving Score (for Leaderboard Town05-long), and L2 distance (for nuScenes Planning).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Stage 2 Input - Consecutive Frames
- **Ablated Part**: Input to the Visual Encoder in Stage 2
- **Action**: REPLACE
- **Replacement**: 
  - Stacked consecutive frames (current and subsequent)
- **Metrics**: Success Rate, Driving Score, L2 (m)

### Ablate Minimum Reprojection and Auto-masking
- **Ablated Part**: Minimum reprojection loss and auto-masking scheme
- **Action**: REMOVE
- **Metrics**: Success Rate, Driving Score, L2 (m)

</div>