<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Learning_to_Prompt_Segmentation_Foundation_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Learning to Prompt Segmentation Foundation Models" proposes SSPrompt, a method for learning spatial and semantic prompts for SFMs. SSPrompt consists of two main components: Spatial Prompt Learning (SpaPrompt) and Semantic Prompt Learning (SemPrompt). Both components optimize learnable prompt embeddings and learnable weights, which are used to fuse the learnable embeddings with the default prompt embeddings (derived from the fixed pre-trained prompt encoders). The paper conducts ablation studies in Table 5 to show the contribution of the learnable embeddings and learnable weights for both spatial and semantic prompt learning, and their combination (SSPrompt). It also compares against vanilla spatial prompt learning (optimizing in 2D space) and prompt engineering.

Based on the analysis of the method and the existing ablations, I identify two important missing ablation studies:

1.  **Contribution of Default Embeddings in Fusion:** The current method fuses learnable embeddings with the *fixed* default embeddings obtained from the pre-trained encoders. The paper argues this selectively leverages pre-trained knowledge. However, an ablation is missing that tests whether using *only* the learnable embeddings (without fusing them with the default ones) is sufficient or if the information from the fixed default embeddings is crucial for performance. The current ablation "Learnable Prompt Embedding" (without weights) seems to average the learnable embedding with the default one (fixed 0.5 weight), which is different from completely removing the default embedding from the fusion process. Testing a setup where the model *only* learns and uses the new embeddings, ignoring the fixed default ones, would directly assess the value of incorporating the pre-trained encoder's output into the learned prompts.

2.  **Sensitivity to the Number of Spatial Prompts:** The paper mentions using N=100 spatial prompts, which seems to be inherited from the default grid size used in SFMs like SEEM. While this number might be reasonable for a grid, it's not clear if it's the optimal number of *learnable* spatial prompt embeddings. An ablation varying the number of learnable spatial prompts (N) would demonstrate the method's sensitivity to this hyperparameter and potentially reveal if a different number could yield better results or computational efficiency.

These two ablations are important because they investigate core design choices: the necessity of fusing with pre-trained embeddings and the impact of a key hyperparameter (number of spatial prompts) on performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Only Learnable Embeddings
- **Ablated Part**: Fusion of learnable embeddings with default prompt embeddings
- **Action**: REMOVE
- **Metrics**: mIoU, AP50, PQ

### Ablation: Number of Spatial Prompts
- **Ablated Part**: Number of learnable spatial prompt embeddings (N)
- **Action**: REPLACE
- **Replacement**: 
  - 25
  - 50
  - 100
  - 200
- **Metrics**: mIoU, AP50, PQ

</div>