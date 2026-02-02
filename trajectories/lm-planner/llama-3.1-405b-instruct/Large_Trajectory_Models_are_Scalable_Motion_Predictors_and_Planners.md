<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Large_Trajectory_Models_are_Scalable_Motion_Predictors_and_Planners

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Large Trajectory Models are Scalable Motion Predictors and Planners" presents a novel approach to motion prediction and planning using large trajectory models. The authors propose a State Transformer (STR) model that reformulates the motion prediction and motion planning problems as a sequence modeling task. The STR model is shown to consistently outperform baseline approaches in both motion planning and motion prediction tasks.

Upon reviewing the paper, I noticed that the authors did not conduct ablation studies on the impact of the Key Points decoder on the overall performance of the STR model. Specifically, it would be interesting to investigate how the number of Key Points affects the model's performance in different scenarios.

Another potential ablation study could focus on the effect of the diffusion-based Key Points decoder on the model's ability to handle multimodal distributions. By comparing the performance of the STR model with and without the diffusion-based decoder, the authors could provide insights into the benefits of using this approach.

Additionally, the authors could explore the impact of different backbone architectures on the STR model's performance. While the GPT-2 model is used as the backbone in the current implementation, it would be interesting to see how other transformer-based architectures, such as BERT or RoBERTa, affect the model's performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Key Points decoder
- **Action**: REMOVE
- **Metrics**: ADE, FDE, MR

### Ablation Study 2
- **Ablated Part**: diffusion-based Key Points decoder
- **Action**: REPLACE
- **Replacement**: 
  - MLP decoder
  - LSTM decoder
- **Metrics**: ADE, FDE, MR

### Ablation Study 3
- **Ablated Part**: GPT-2 backbone
- **Action**: REPLACE
- **Replacement**: 
  - BERT backbone
  - RoBERTa backbone
- **Metrics**: ADE, FDE, MR

</div>