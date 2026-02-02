<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/componet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose a set of ablation studies that target the core components responsible for knowledge transfer and module composition in CompoNet. The first study removes the output attention head, which is responsible for aggregating previous policies’ outputs based on the current state. Its removal will reveal how crucial this aggregation is for accelerated learning and overall performance. Next, we propose removing the input attention head, which integrates the tentative output and previous policy information to guide the internal policy; its absence should highlight its effect on the stability and quality of the composed policy. Another critical component is the cosine positional encoding used within the attention mechanisms: by replacing it with alternatives (or removing it), we can assess the influence of the alignment mechanism on both performance and inference speed. Finally, the freezing of previous modules is a cornerstone of CompoNet that prevents catastrophic forgetting. By allowing these modules to remain trainable (or partially trainable), we can observe the trade-offs between stability and plasticity. These studies will report standard metrics including cumulative reward, knowledge transfer efficiency, learning speed, catastrophic forgetting, and inference time as used in the paper.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Remove Output Attention Head
- **Ablated Part**: The output attention head that generates a tentative output based on previous modules’ outputs and the current state
- **Action**: REMOVE
- **Metrics**: cumulative_reward, transfer_efficiency, learning_speed

### Ablation 2: Remove Input Attention Head
- **Ablated Part**: The input attention head that fuses the tentative output with past policy outputs to guide the internal policy
- **Action**: REMOVE
- **Metrics**: cumulative_reward, knowledge_transfer, policy_stability

### Ablation 3: Replace Cosine Positional Encoding
- **Ablated Part**: The cosine positional encoding in the attention heads used to align previous policy outputs
- **Action**: REPLACE
- **Replacement**: 
  - None
  - learned positional embeddings
  - sinusoidal encoding
- **Metrics**: cumulative_reward, inference_time, model_performance

### Ablation 4: Unfreeze Previous Modules
- **Ablated Part**: The freezing mechanism on previously learned policy modules to prevent catastrophic forgetting
- **Action**: REPLACE
- **Replacement**: 
  - fully trainable
  - partially trainable
- **Metrics**: catastrophic_forgetting, cumulative_reward, learning_speed

</div>