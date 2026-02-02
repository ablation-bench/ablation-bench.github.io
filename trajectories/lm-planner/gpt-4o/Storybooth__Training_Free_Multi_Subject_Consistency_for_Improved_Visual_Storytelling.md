<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Storybooth__Training_Free_Multi_Subject_Consistency_for_Improved_Visual_Storytelling

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Storybooth: Training-Free Multi-Subject Consistency for Improved Visual Storytelling" introduces a novel approach to improve multi-character consistency in text-to-image generation without requiring training or optimization. The method leverages a modified diffusion model with a bounded cross-attention layer and a cross-frame token-merging layer to address self-attention leakage and improve fine-grain consistency. The paper includes ablation studies on the importance of self-attention bounding, token-merging, and early negative token unmerging.

The existing ablation studies focus on:
1. The role of self-attention bounding in reducing inter-character leakage.
2. The impact of token-merging on aligning fine-grain character features.
3. The effect of early negative token unmerging on increasing pose variance.

However, there are some components and design choices in the method that could benefit from further ablation studies to better understand their contributions:

1. **Region-Based Planning and Generation**: The method uses region-based planning to localize subjects across storyboard frames. An ablation study could explore the impact of this component by removing it and observing changes in character consistency and text-to-image alignment.

2. **Dropout in Self-Attention**: The paper introduces a dropout term in the self-attention computation to preserve image quality while reducing inter-character leakage. An ablation study could investigate the effect of varying dropout probabilities on the method's performance.

These additional ablation studies would provide a more comprehensive understanding of the method's components and their contributions to the overall performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Region-Based Planning
- **Ablated Part**: Region-based planning and generation
- **Action**: REMOVE
- **Metrics**: T2I Alignment, Character Consistency

### Ablation of Dropout in Self-Attention
- **Ablated Part**: Dropout term in self-attention computation
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.1
  - 0.2
  - 0.3
- **Metrics**: T2I Alignment, Character Consistency

</div>