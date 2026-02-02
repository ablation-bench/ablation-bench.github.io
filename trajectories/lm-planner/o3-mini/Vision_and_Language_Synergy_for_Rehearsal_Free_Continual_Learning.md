<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Vision_and_Language_Synergy_for_Rehearsal_Free_Continual_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One key component of LEAPGen is that task‐specific parameters – the prompt generator networks and the associated task/class keys – are frozen immediately after training on each task, with the aim of preserving performance and preventing interference from subsequently learned tasks. However, the paper does not report an ablation study that removes or relaxes this freezing mechanism to directly quantify its importance. Removing the freezing constraint could lead to increased flexibility during training, but will likely incur higher catastrophic forgetting. Assessing this variation will provide valuable insight into how critical freezing of these components is to the overall stability of the continual learning system.

Another important component is the use of language as input for prompt generation. While the paper does evaluate an alternative version (LEAPGen-CN) using class names as descriptors, it does not explore the sensitivity of the system to the quality of the language descriptors. Replacing meaningful descriptors with random or scrambled text – which lacks semantic grounding – should substantially affect performance. Such an ablation will help underline the role of high-quality, semantically rich language descriptions in guiding prompt generation and ultimately in mitigating forgetting.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Freezing Task-specific Parameters
- **Ablated Part**: Freezing of task-wise generators and associated keys (task-specific generator networks, task key K^t, and class key L^t) after each task
- **Action**: REMOVE
- **Metrics**: FAA, CAA, FFM, CFM

### Ablation on Language Descriptor Quality
- **Ablated Part**: Quality of language descriptors used as input for prompt generation
- **Action**: REPLACE
- **Replacement**: 
  - Random vectors
  - Scrambled class names
- **Metrics**: FAA, CAA, FFM, CFM

</div>