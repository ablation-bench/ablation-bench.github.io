<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Mousterian__exploring_the_equivalence_of_generative_and_real_data_augmentation_in_classification

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper investigates how generative data augmentation can enhance image classification performance. After reviewing the paper, I notice a few key missing ablation studies:

1. The paper uses different text prompts for generating synthetic data (simple class-conditioned prompts vs diverse captions), but doesn't systematically ablate the impact of prompt engineering on the final classification performance. This is important since prompt design can significantly affect the quality and diversity of generated images.

2. The paper uses different mixing strategies for combining real and synthetic data (using PyTorch's ConcatDataset with random sampling), but doesn't investigate alternative mixing strategies that could potentially handle the domain gap between real and synthetic data better. This is particularly important given their finding that real and synthetic data exist on distinct manifolds.

I believe these are the two most important missing ablations that could provide valuable insights into the method's performance. The first ablation would help understand how much prompt engineering matters for classification performance, while the second would investigate if more sophisticated mixing strategies could better leverage synthetic data.

The metrics used in the paper are primarily Top-1 and Top-5 accuracy for classification performance, and FID/IS scores for evaluating synthetic data quality. We should maintain these metrics for consistency.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Prompt Engineering Ablation
- **Ablated Part**: text prompts used for generating synthetic data
- **Action**: REPLACE
- **Replacement**: 
  - simple class name prompt
  - template-based diverse captions
  - ChatGPT-generated diverse captions
- **Metrics**: Top-1 Accuracy, Top-5 Accuracy, FID, IS

### Data Mixing Strategy Ablation
- **Ablated Part**: strategy for combining real and synthetic data during training
- **Action**: REPLACE
- **Replacement**: 
  - random sampling
  - balanced sampling
  - curriculum learning (starting with more real data)
  - weighted sampling based on FID scores
- **Metrics**: Top-1 Accuracy, Top-5 Accuracy

</div>