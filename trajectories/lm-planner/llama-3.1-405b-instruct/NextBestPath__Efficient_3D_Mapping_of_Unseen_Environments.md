<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/NextBestPath__Efficient_3D_Mapping_of_Unseen_Environments

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "NextBestPath: Efficient 3D Mapping of Unseen Environments" presents a novel approach for active 3D mapping, which involves predicting long-term goals rather than focusing solely on short-sighted views. The authors propose a new method called next-best-path (NBP), which jointly predicts accumulated surface coverage gains for long-term goals and obstacle maps, allowing it to efficiently plan optimal paths with a unified model.

The paper also introduces a new dataset called AiMDoom, which is designed to benchmark active 3D mapping in diverse indoor environments. The dataset includes four levels of geometric complexity, with various textures and layouts.

The authors evaluate their method on both the existing MP3D dataset and their AiMDoom dataset, achieving state-of-the-art results. However, they also note that there is still room for improvement, particularly in more complex environments.

To further improve the method, we suggest two missing ablation studies:

1. Investigating the impact of different spatial ranges for the prediction of the value map and obstacle map on the performance of the NBP method. This could involve training and evaluating the model with different spatial ranges, such as 20m × 20m, 30m × 30m, 40m × 40m, and 50m × 50m.
2. Evaluating the effectiveness of the NBP method with different strategies for updating long-term goals during inference. This could involve comparing the performance of the original strategy, which updates long-term goals upon completing a path, with a new strategy that updates goals at each step.

These ablation studies could provide valuable insights into the strengths and weaknesses of the NBP method and help identify areas for further improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Spatial range of value map and obstacle map
- **Action**: REPLACE
- **Replacement**: 
  - 20m × 20m
  - 30m × 30m
  - 40m × 40m
  - 50m × 50m
- **Metrics**: Final Coverage, AUCs

### Ablation Study 2
- **Ablated Part**: Strategy for updating long-term goals
- **Action**: REPLACE
- **Replacement**: 
  - Original strategy
  - New strategy
- **Metrics**: Final Coverage, AUCs

</div>