<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Tell_me_about_yourself__LLMs_are_aware_of_their_learned_behaviors

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Looking at the paper's methodology and experiments, I notice a few key components that weren't ablated but could provide important insights:

1. The most critical missing ablation is on the finetuning data size. While there is a brief mention of an ablation with 32-128 datapoints for the multiple-choice experiment (Table 17), there is no systematic ablation of data size for the more complex dialogue-based experiments ("Make Me Say" game). This is important because understanding how much data is needed for behavioral self-awareness to emerge could provide insights into whether this capability requires extensive training or can emerge from minimal examples.

2. Another important missing ablation is on the model's ability to articulate its policy without any prompting. In the current setup, the model is always explicitly asked about its behavior/goals through direct questions. An ablation where the model needs to volunteer information about its policy (e.g., in a more open-ended conversation) would help understand if behavioral self-awareness emerges naturally or requires explicit prompting.

I'll focus on suggesting the data size ablation since it appears more fundamental to understanding the emergence of behavioral self-awareness.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Data Size Ablation
- **Ablated Part**: number of training dialogues in Make Me Say game
- **Action**: REPLACE
- **Replacement**: 
  - 50 dialogues
  - 200 dialogues
  - 500 dialogues
- **Metrics**: win rate in Make Me Say game, accuracy on policy description tasks, accuracy on codeword identification

### Unprompted Policy Description
- **Ablated Part**: explicit questions about model's policy
- **Action**: REPLACE
- **Replacement**: 
  - open-ended conversation prompts
  - indirect questions about model's behavior
- **Metrics**: rate of policy disclosure, accuracy of policy descriptions when disclosed

</div>