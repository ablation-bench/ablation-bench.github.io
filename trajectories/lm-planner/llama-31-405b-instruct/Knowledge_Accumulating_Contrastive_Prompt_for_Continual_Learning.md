<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Knowledge_Accumulating_Contrastive_Prompt_for_Continual_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Knowledge Accumulating Contrastive Prompt for Continual Learning" proposes a novel approach to prompt-based continual learning, which accumulates knowledge in a single prompt. The method uses contrastive learning to pull the features of the positive pairs in the embedding space to accumulate knowledge. The paper demonstrates the state-of-the-art performance in continual learning even with a single prompt, highlighting the potential of this approach towards a 'holistic' prompt for the model.

To further investigate the effectiveness of this approach, we suggest two missing ablation studies:

1. Ablation study on the impact of the prompt length on the performance of the model. The paper uses a fixed prompt length, but it would be interesting to see how the performance changes with different prompt lengths.
2. Ablation study on the impact of the number of previous tasks on the performance of the model. The paper uses a fixed number of previous tasks, but it would be interesting to see how the performance changes with different numbers of previous tasks.

These ablation studies would provide more insights into the effectiveness of the proposed approach and help to identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: prompt length
- **Action**: REPLACE
- **Replacement**: 
  - 5
  - 10
  - 20
  - 40
- **Metrics**: Average Accuracy, Forgetting

### Ablation Study 2
- **Ablated Part**: number of previous tasks
- **Action**: REPLACE
- **Replacement**: 
  - 2
  - 5
  - 10
- **Metrics**: Average Accuracy, Forgetting

</div>