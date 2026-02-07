<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/LLM_as_a_Complementary_Optimizer_to_Gradient_Descent__A_Case_Study_in_Prompt_Tuning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that while the authors conduct several ablation studies on various components like instruction design, optimization rounds, and timing of interactions, there are two critical aspects of their method that lack thorough ablation analysis:

1. The impact of the optimization trajectory information provided to the LLM:
The authors mention they provide "intermediate optimized prompt in the training trajectory" and "fitness scores" to the LLM, but don't ablate how much trajectory information is optimal. This is crucial since it directly affects how the LLM reasons about generating better prompts.

2. The effect of different prompt selection strategies after LLM generation:
The paper mentions that LLM generates multiple candidate prompts (3 as shown in Figure 3), but doesn't analyze how these candidates are selected for the next gradient optimization round. Understanding the impact of different selection strategies would be valuable.

These ablations would help better understand the key mechanisms of the method and potentially improve its performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Trajectory Length Ablation
- **Ablated Part**: Amount of optimization trajectory information provided to LLM
- **Action**: REPLACE
- **Replacement**: 
  - Last 1 prompt
  - Last 3 prompts
  - Last 5 prompts
  - All prompts
- **Metrics**: Accuracy, Loss

### Prompt Selection Strategy Ablation
- **Ablated Part**: Strategy for selecting LLM-generated prompts for next optimization round
- **Action**: REPLACE
- **Replacement**: 
  - Random selection
  - Best performing on validation
  - Ensemble of all candidates
  - Most semantically different from previous
- **Metrics**: Accuracy, Loss

</div>