<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/hdnet_tiktok

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents a novel approach to estimate high fidelity depths of dressed humans from single view images by leveraging social media dance videos. The method addresses the challenge of limited ground truth data by using self-supervision through temporal coherence and joint learning of depth and surface normals. The key components of the method include the use of local transformations for self-supervision, joint learning of depth and surface normals, and the HDNet architecture.

To design ablation studies, we should focus on these key components to understand their contribution to the overall performance. The ablation studies should aim to isolate the effect of each component by either removing, replacing, or adding elements to the method. The metrics to report should include depth error, normal error, and reconstruction error, as these are the primary metrics used in the paper.

1. Ablation of the local transformation for self-supervision: This component is crucial for utilizing the dance videos without 3D ground truth. Removing this component will help understand its impact on the model's ability to learn from video data.

2. Ablation of joint learning of depth and surface normals: This component is responsible for capturing fine details in the geometry. Replacing this with separate learning of depth and normals will help assess the importance of joint learning.

3. Ablation of the HDNet architecture: The architecture is designed to enforce geometric consistency and leverage both real videos and 3D scanned models. Removing or modifying parts of the architecture can reveal its contribution to the method's performance.

4. Ablation of the TikTok dataset: The dataset is a significant part of the method, providing diverse data for training. Removing or replacing it with a different dataset can show its impact on generalization and performance.

5. Ablation of the loss function components: The loss function includes several terms for self-consistency and supervision. Removing or altering these terms can help understand their role in training the model effectively.

These ablation studies will provide insights into the importance of each component and guide future improvements to the method.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Local Transformation
- **Ablated Part**: Local transformation for self-supervision
- **Action**: REMOVE
- **Metrics**: depth error, normal error, reconstruction error

### Ablation of Joint Learning
- **Ablated Part**: Joint learning of depth and surface normals
- **Action**: REPLACE
- **Replacement**: 
  - Separate learning of depth and normals
- **Metrics**: depth error, normal error, reconstruction error

### Ablation of HDNet Architecture
- **Ablated Part**: HDNet architecture
- **Action**: REMOVE
- **Metrics**: depth error, normal error, reconstruction error

### Ablation of TikTok Dataset
- **Ablated Part**: TikTok dataset
- **Action**: REMOVE
- **Metrics**: depth error, normal error, reconstruction error

### Ablation of Loss Function Components
- **Ablated Part**: Loss function components
- **Action**: REMOVE
- **Metrics**: depth error, normal error, reconstruction error

</div>