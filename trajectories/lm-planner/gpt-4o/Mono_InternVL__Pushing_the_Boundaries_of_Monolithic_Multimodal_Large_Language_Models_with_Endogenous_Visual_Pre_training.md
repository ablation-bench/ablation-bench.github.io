<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Mono_InternVL__Pushing_the_Boundaries_of_Monolithic_Multimodal_Large_Language_Models_with_Endogenous_Visual_Pre_training

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Mono-InternVL: Pushing the Boundaries of Monolithic Multimodal Large Language Models with Endogenous Visual Pre-training" introduces a novel monolithic MLLM that integrates visual encoding and language decoding into a single LLM. The key innovations include embedding visual experts into a pre-trained LLM using a multimodal mixture-of-experts structure and an innovative pre-training strategy called Endogenous Visual Pre-training (EViP). The paper conducts extensive experiments and ablation studies to validate the effectiveness of these components.

The existing ablation studies in the paper focus on the strategies for visual pre-training, comparing full tuning and delta tuning, and the impact of freezing and unfreezing attention layers during alignment learning. These studies highlight the importance of visual experts and the delta tuning strategy in preserving language understanding capabilities while enhancing visual learning.

However, there are some missing ablation studies that could provide further insights into the method's performance. One potential ablation study could involve the removal of the multimodal mixture-of-experts structure to assess its impact on the model's performance. This would help to understand the significance of this structure in facilitating visual pre-training and mitigating catastrophic forgetting. Another potential ablation study could involve replacing the endogenous visual pre-training strategy with alternative pre-training strategies to evaluate the effectiveness of EViP in maximizing visual capability.

These missing ablation studies would help to attribute the method's performance to its major components and provide a more comprehensive understanding of the contributions of the proposed innovations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Multimodal mixture-of-experts structure
- **Action**: REMOVE
- **Metrics**: MME-P, DocVQA, InfoVQA, SQA-I, GQA, ChartQA, AI2D

### Ablation 2
- **Ablated Part**: Endogenous Visual Pre-training (EViP)
- **Action**: REPLACE
- **Replacement**: 
  - Native Pre-training
  - Continuous Pre-training
- **Metrics**: MME-P, DocVQA, InfoVQA, SQA-I, GQA, ChartQA, AI2D

</div>