<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/LVLM_CL__Make_Large_Vision_Language_Models_Work_Better_under_Continual_Learning_Settings

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that the method has two main components:
1. A text feature-based prompt system that differs between tasks to maintain task-specific features
2. A memory bank that stores previous trained tasks

The paper already includes some ablation studies:
- Memory bank size (M=0%, 5%, 10%)
- Hyperparameter α that controls information retention (0.1, 0.3, 0.5, 0.7, 0.9)
- Task ordering effects

However, I identify two critical missing ablations:

1. The most important missing ablation is on the text feature-based prompt system, which is a core component but was not ablated. We should test how the model performs without task-specific prompts to validate their importance.

2. The second important missing ablation would be on the concentration learning module that constructs task-invariant features. This module is crucial for maintaining knowledge across tasks but was not evaluated in isolation.

I'll prioritize these two ablations, with the prompt system being more fundamental to the method's performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Task-Specific Prompt Ablation
- **Ablated Part**: text feature-based prompt system
- **Action**: REMOVE
- **Metrics**: VQA-v2 accuracy, GQA accuracy, VizWiz accuracy, SciQA accuracy, MME score, MMBench score, POPE accuracy, MM-Vet accuracy

### Concentration Learning Module Ablation
- **Ablated Part**: concentration learning module for task-invariant features
- **Action**: REMOVE
- **Metrics**: VQA-v2 accuracy, GQA accuracy, VizWiz accuracy, SciQA accuracy, MME score, MMBench score, POPE accuracy, MM-Vet accuracy

</div>