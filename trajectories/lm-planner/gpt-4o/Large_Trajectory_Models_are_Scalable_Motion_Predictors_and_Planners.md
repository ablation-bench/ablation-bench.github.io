<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Large_Trajectory_Models_are_Scalable_Motion_Predictors_and_Planners

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Large Trajectory Models are Scalable Motion Predictors and Planners" introduces the State Transformer (STR) for motion prediction and planning in autonomous driving. The paper highlights the scalability of STR and its superior performance compared to existing benchmarks. The ablation studies conducted in the paper focus on the impact of Key Points and diffusion decoders on performance. However, there are some areas where additional ablation studies could provide further insights into the model's performance.

Firstly, the paper mentions the use of a causal transformer backbone, specifically the GPT-2 model, for sequence modeling. An ablation study could investigate the impact of different transformer architectures on the model's performance. This would help determine if the choice of GPT-2 is optimal or if other architectures could offer better performance.

Secondly, the paper introduces Proposals and Key Points as part of the sequence modeling task. While the impact of Key Points is studied, the role of Proposals in guiding the model's predictions is not thoroughly explored. An ablation study could examine the effect of removing or modifying the Proposals component to understand its contribution to the model's performance.

These additional ablation studies would provide a more comprehensive understanding of the STR's design choices and their impact on performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study on Transformer Backbone
- **Ablated Part**: Causal Transformer Backbone
- **Action**: REPLACE
- **Replacement**: 
  - BERT
  - Transformer-XL
  - T5
- **Metrics**: ADE, FDE, mAP, MR

### Ablation Study on Proposals
- **Ablated Part**: Proposals Component
- **Action**: REMOVE
- **Metrics**: ADE, FDE, mAP, MR

</div>