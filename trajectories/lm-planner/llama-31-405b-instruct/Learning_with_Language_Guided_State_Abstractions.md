<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Learning_with_Language_Guided_State_Abstractions

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Learning with Language-Guided State Abstractions" presents a framework for using natural language to design state abstractions for imitation learning. The authors propose a method called Language-Guided Abstraction (LGA), which uses a combination of natural language supervision and background knowledge from language models to automatically build state representations tailored to unseen tasks.

The paper evaluates LGA on simulated robotic tasks and shows that it yields state abstractions similar to those designed by humans, but in a fraction of the time. The authors also demonstrate the utility of the learned abstractions on mobile manipulation tasks with a Spot robot.

To further investigate the effectiveness of LGA, I suggest two missing ablation studies:

1. **Ablation of Language Model Size**: The current study uses a specific language model (GPT4) to generate state abstractions. It would be interesting to see how the performance of LGA changes with different language model sizes. This ablation study would help understand the impact of language model capacity on the quality of state abstractions.
2. **Ablation of State Abstraction Granularity**: The current study uses a specific granularity for state abstractions (e.g., object types and colors). It would be interesting to see how the performance of LGA changes with different levels of granularity. This ablation study would help understand the trade-off between abstraction granularity and policy performance.

These ablation studies would provide valuable insights into the robustness and generalizability of LGA and help identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Language Model Size
- **Ablated Part**: language model size
- **Action**: REPLACE
- **Replacement**: 
  - small
  - medium
  - large
- **Metrics**: task performance, user time

### Ablation of State Abstraction Granularity
- **Ablated Part**: state abstraction granularity
- **Action**: REPLACE
- **Replacement**: 
  - coarse
  - fine
- **Metrics**: task performance, policy robustness

</div>