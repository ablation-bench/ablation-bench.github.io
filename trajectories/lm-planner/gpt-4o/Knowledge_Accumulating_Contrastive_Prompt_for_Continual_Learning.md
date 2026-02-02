<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Knowledge_Accumulating_Contrastive_Prompt_for_Continual_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Knowledge Accumulating Contrastive Prompt for Continual Learning" introduces a novel approach to continual learning by accumulating knowledge in a single prompt using contrastive learning techniques. The method aims to address catastrophic forgetting by treating inputs with current and previous prompts as positive pairs and pulling their features closer in the embedding space. The paper already includes several ablation studies, such as the impact of varying the task number and the effect of different hyperparameters like λ_prev. However, there are still some missing ablation studies that could provide further insights into the method's effectiveness.

One potential missing ablation study is the examination of the impact of the contrastive loss function used. The paper employs a positive-only contrastive loss inspired by SimSiam, but it would be valuable to explore how different contrastive loss functions, such as InfoNCE or Barlow Twins, affect the performance. This would help determine if the choice of contrastive loss is critical to the method's success.

Another missing ablation study could focus on the role of the prompt length and its distribution across layers. The paper uses a specific configuration for prompt length across different layers, but it would be insightful to investigate how varying these lengths or using a uniform length across all layers impacts the model's performance. This could reveal the sensitivity of the method to the prompt configuration and help optimize the prompt design.

These ablation studies are important as they can provide a deeper understanding of the method's components and their contributions to mitigating catastrophic forgetting in continual learning.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study on Contrastive Loss Function
- **Ablated Part**: contrastive loss function used in the method
- **Action**: REPLACE
- **Replacement**: 
  - InfoNCE
  - Barlow Twins
  - VICReg
- **Metrics**: Average Accuracy, Forgetting

### Ablation Study on Prompt Length Configuration
- **Ablated Part**: prompt length and its distribution across layers
- **Action**: REPLACE
- **Replacement**: 
  - Uniform length across all layers
  - Different lengths for each layer
- **Metrics**: Average Accuracy, Forgetting

</div>