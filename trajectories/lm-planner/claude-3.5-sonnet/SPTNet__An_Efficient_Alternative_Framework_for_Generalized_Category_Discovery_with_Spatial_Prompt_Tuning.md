<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/SPTNet__An_Efficient_Alternative_Framework_for_Generalized_Category_Discovery_with_Spatial_Prompt_Tuning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that there are two major components that could benefit from additional ablation studies:

1. The Two-Stage Alternative Training Strategy:
The paper proposes a novel two-stage training approach that alternates between optimizing model parameters and data parameters (prompts). While they show some ablations comparing different training strategies in Table 5, they don't fully investigate how the order and frequency of alternating between stages affects performance. This is important since it's a key contribution of their method.

2. The Spatial Prompt Architecture:
While they ablate the prompt size and some configurations, they don't investigate the impact of different spatial prompt architectures/patterns. The current design attaches prompts to each patch in a rectangular shape, but alternative spatial arrangements could potentially improve performance. This is particularly important since the spatial aspect is one of their main novelties.

Based on these observations, I'll suggest two key missing ablation studies, ranked by importance:

1. A more thorough investigation of the two-stage training dynamics, as this is central to their method's performance.
2. An exploration of different spatial prompt architectures, as this could potentially improve their method further.

The metrics used should match those reported in the paper: clustering accuracy (ACC) for "All", "Old" and "New" classes.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Two-Stage Training Dynamics Ablation
- **Ablated Part**: two-stage alternative training strategy
- **Action**: REPLACE
- **Replacement**: 
  - sequential stages (first model then prompts)
  - sequential stages (first prompts then model)
  - concurrent optimization of both
  - alternating every 5 iterations
  - alternating every 50 iterations
- **Metrics**: ACC_all, ACC_old, ACC_new

### Spatial Prompt Architecture Ablation
- **Ablated Part**: spatial prompt pattern design
- **Action**: REPLACE
- **Replacement**: 
  - circular pattern around patches
  - diagonal pattern
  - cross pattern
  - adaptive pattern based on image content
- **Metrics**: ACC_all, ACC_old, ACC_new

</div>