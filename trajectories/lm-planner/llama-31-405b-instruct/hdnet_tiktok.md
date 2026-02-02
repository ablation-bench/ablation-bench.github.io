<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/hdnet_tiktok

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

To design ablation studies for the research titled "Learning High Fidelity Depths of Dressed Humans by Watching Social Media Dance Videos," we need to identify the key components of the method and then propose experiments to evaluate their impact on the overall performance. The method uses a combination of self-supervision from videos and joint learning of surface normals and depths to predict high-fidelity depths of dressed humans from a single view image.

1. **Self-supervision from videos**: The method uses self-supervision from videos to learn the depth estimation without requiring ground truth depth data. An ablation study could investigate the impact of removing this self-supervision component on the performance of the depth estimation.

2. **Joint learning of surface normals and depths**: The method jointly learns surface normals and depths to benefit from each other. An ablation study could explore the effect of learning these components separately versus jointly.

3. **Use of surface normals**: The method uses surface normals to enhance the depth estimation. An ablation study could examine the impact of not using surface normals on the accuracy of the depth estimation.

4. **Part-based transformation**: The method uses a part-based transformation to warp the predicted local geometry of the person from one image to another at a different time instant. An ablation study could investigate the effect of using a global transformation instead of a part-based transformation.

5. **Dataset size**: The method is trained on a large dataset of social media dance videos. An ablation study could explore how the size of the training dataset affects the performance of the depth estimation.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Self-supervision from videos
- **Action**: REMOVE
- **Metrics**: depth error, normal error, reconstruction error

### Ablation 2
- **Ablated Part**: Joint learning of surface normals and depths
- **Action**: REPLACE
- **Replacement**: 
  - learning surface normals and depths separately
- **Metrics**: depth error, normal error, reconstruction error

### Ablation 3
- **Ablated Part**: Use of surface normals
- **Action**: REMOVE
- **Metrics**: depth error, reconstruction error

### Ablation 4
- **Ablated Part**: Part-based transformation
- **Action**: REPLACE
- **Replacement**: 
  - global transformation
- **Metrics**: depth error, reconstruction error

### Ablation 5
- **Ablated Part**: Dataset size
- **Action**: ADD
- **Replacement**: 
  - half of the original dataset size
  - quarter of the original dataset size
- **Metrics**: depth error, normal error, reconstruction error

</div>