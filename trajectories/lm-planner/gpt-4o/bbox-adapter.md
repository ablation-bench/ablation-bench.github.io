<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/bbox-adapter

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The BBox-Adapter method introduces a novel approach to adapt black-box LLMs by using a lightweight adapter that employs a ranking-based Noise Contrastive Estimation (NCE) loss. The method distinguishes between target and source domain data and features an online adaptation mechanism. The key components of the method include the ranking-based NCE loss, the online adaptation framework, and the use of AI feedback for positive data sampling. To understand the contribution of each component to the overall performance, we can design ablation studies focusing on these components.

1. **Ranking-based NCE Loss**: This is a critical component that helps in distinguishing between the source and target domain data. An ablation study could involve replacing the ranking-based NCE loss with a standard NCE loss or other loss functions to evaluate its impact on performance.

2. **Online Adaptation Mechanism**: This mechanism allows the model to incorporate real-time positive data sampling and update the adapter iteratively. An ablation study could involve removing the online adaptation mechanism to see how it affects the model's ability to adapt to new data.

3. **AI Feedback for Positive Data Sampling**: The use of AI feedback is a novel aspect of the method that reduces reliance on ground-truth data. An ablation study could involve replacing AI feedback with human feedback or removing feedback altogether to assess its impact on the adaptation process.

4. **Adapter Size**: The method uses a small adapter model with 0.1B-0.3B parameters. An ablation study could involve varying the size of the adapter to understand the trade-off between model size and performance.

5. **Beam Search Process**: The method uses a sentence-level beam search process during inference. An ablation study could involve removing the beam search process to evaluate its contribution to the model's performance.

These ablation studies will help in understanding the importance of each component and guide future improvements to the BBox-Adapter method.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Ranking-based NCE Loss
- **Action**: REPLACE
- **Replacement**: 
  - Standard NCE Loss
  - Cross-Entropy Loss
- **Metrics**: Accuracy, Training Cost, Inference Cost

### Ablation 2
- **Ablated Part**: Online Adaptation Mechanism
- **Action**: REMOVE
- **Metrics**: Accuracy, Training Cost, Inference Cost

### Ablation 3
- **Ablated Part**: AI Feedback for Positive Data Sampling
- **Action**: REPLACE
- **Replacement**: 
  - Human Feedback
  - No Feedback
- **Metrics**: Accuracy, Training Cost, Inference Cost

### Ablation 4
- **Ablated Part**: Adapter Size
- **Action**: REPLACE
- **Replacement**: 
  - 0.05B Parameters
  - 0.5B Parameters
- **Metrics**: Accuracy, Training Cost, Inference Cost

### Ablation 5
- **Ablated Part**: Beam Search Process
- **Action**: REMOVE
- **Metrics**: Accuracy, Training Cost, Inference Cost

</div>