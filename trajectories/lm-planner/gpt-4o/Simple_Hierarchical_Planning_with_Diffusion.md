<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Simple_Hierarchical_Planning_with_Diffusion

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Simple Hierarchical Planning with Diffusion" introduces the Hierarchical Diffuser, which combines hierarchical and diffusion-based planning to address computational challenges and improve generalization in long-horizon tasks. The method involves a high-level "jumpy" planning strategy and a low-level planner for fine-tuning. The paper includes several ablation studies, such as the impact of dense actions and the effect of different kernel sizes on performance. However, there are still some missing ablation studies that could provide further insights into the method's components.

One potential missing ablation study is the impact of the "jumpy" planning strategy itself. The paper emphasizes the importance of this strategy for reducing computational costs and improving the receptive field, but it does not explicitly ablate this component to assess its individual contribution to the overall performance. Removing or modifying the jumpy planning strategy could help isolate its effects and validate the claims made about its benefits.

Another missing ablation study could focus on the role of the guidance function in the hierarchical planning framework. The guidance function is crucial for directing the planning process towards high-return trajectories, but its specific impact on the hierarchical diffuser's performance is not thoroughly explored. Replacing or modifying the guidance function with alternative strategies could provide insights into its necessity and effectiveness.

These ablation studies would help attribute the method's performance to its major components and validate the design choices made in the Hierarchical Diffuser.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Jumpy Planning Strategy
- **Ablated Part**: High-level jumpy planning strategy
- **Action**: REMOVE
- **Metrics**: training_speed, planning_speed, generalization_performance, task_success_rate

### Ablation of Guidance Function
- **Ablated Part**: Guidance function in hierarchical planning
- **Action**: REPLACE
- **Replacement**: 
  - random_guidance
  - fixed_guidance
  - no_guidance
- **Metrics**: expected_return, task_success_rate, generalization_performance

</div>