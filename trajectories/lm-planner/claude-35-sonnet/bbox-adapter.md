<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/bbox-adapter

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, BBox-AdAPTER has several key components that warrant investigation through ablation studies:

1. The most critical component is the ranking-based NCE loss, which is fundamental to the method's ability to distinguish between target and source domain data. The paper already shows its importance compared to MLM loss in Table 4, but further investigation would be valuable.

2. The online adaptation mechanism is another core component that iteratively samples from previous inferences and updates the adapter. Testing the model without this component would help quantify its contribution.

3. The method uses both ground truth and AI feedback for positive samples. Understanding the relative importance of each feedback source would be valuable.

4. The adapter size (0.1B vs 0.3B parameters) appears to impact performance differently across tasks. A systematic investigation of adapter sizes would be useful.

5. The beam search process during inference is an important component that affects the final output quality.

I'll suggest ablation studies for these components, focusing on the most important aspects first.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### NCE Loss Ablation
- **Ablated Part**: ranking-based NCE loss
- **Action**: REPLACE
- **Replacement**: 
  - Cross-Entropy Loss
  - Contrastive Loss
  - MSE Loss
- **Metrics**: Accuracy (%), True + Info (%)

### Online Adaptation Ablation
- **Ablated Part**: online adaptation mechanism
- **Action**: REMOVE
- **Metrics**: Accuracy (%), True + Info (%), Training Cost ($), Inference Cost ($)

### Feedback Source Ablation
- **Ablated Part**: feedback sources for positive samples
- **Action**: REPLACE
- **Replacement**: 
  - Ground-Truth Only
  - AI Feedback Only
  - Combined Feedback
- **Metrics**: Accuracy (%), True + Info (%)

### Adapter Size Study
- **Ablated Part**: adapter model size
- **Action**: REPLACE
- **Replacement**: 
  - 0.05B
  - 0.1B
  - 0.3B
  - 0.5B
- **Metrics**: Accuracy (%), True + Info (%), VRAM (GiB)

### Beam Search Ablation
- **Ablated Part**: beam search during inference
- **Action**: REPLACE
- **Replacement**: 
  - Greedy Search
  - Nucleus Sampling
  - Temperature Sampling
- **Metrics**: Accuracy (%), True + Info (%), Inference Cost ($)

</div>