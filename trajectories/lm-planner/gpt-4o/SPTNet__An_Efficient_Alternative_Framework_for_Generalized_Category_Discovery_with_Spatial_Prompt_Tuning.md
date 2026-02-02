<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/SPTNet__An_Efficient_Alternative_Framework_for_Generalized_Category_Discovery_with_Spatial_Prompt_Tuning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "SPTNet: An Efficient Alternative Framework for Generalized Category Discovery with Spatial Prompt Tuning" introduces a novel approach to Generalized Category Discovery (GCD) by optimizing both model and data parameters through a two-stage iterative learning framework. The key innovation is the Spatial Prompt Tuning (SPT), which adapts data representation to align better with pre-trained models by focusing on spatial properties of image data. The paper includes several ablation studies to evaluate the effectiveness of different components, such as the impact of prompt-related techniques and training strategies.

The existing ablation studies in the paper focus on:
1. The effect of different prompting methods, including Visual Prompt Tuning (VPT), global prompts, and the proposed SPT.
2. The impact of different training strategies, such as end-to-end, data-first, model-first, and alternative training.
3. The effects of alternating frequency and prompt size on performance.

However, there are some missing ablation studies that could provide further insights into the method's performance. One potential area for ablation is the specific contribution of the global prompt in conjunction with the spatial prompt. Another area is the exploration of different spatial prompt configurations, such as varying the number of learnable parameters or the shape of the prompts.

These missing ablations could help in understanding the individual contributions of each component and their interactions, which is crucial for optimizing the method further.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Global Prompt
- **Ablated Part**: Global prompt in conjunction with spatial prompt
- **Action**: REMOVE
- **Metrics**: ACC

### Ablation of Spatial Prompt Configuration
- **Ablated Part**: Configuration of spatial prompts
- **Action**: REPLACE
- **Replacement**: 
  - fewer parameters
  - different shapes
- **Metrics**: ACC

</div>