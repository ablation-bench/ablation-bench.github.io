<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Vision_and_Language_Synergy_for_Rehearsal_Free_Continual_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents a novel prompt-based method for continual learning called LEAPGen with 4 key components:
1. Language as input for prompt generation
2. Task-wise generators
3. Soft task-id prediction using both task-wise and class-wise keys
4. Generated prompt as auxiliary data

Looking at the existing ablation studies in Table 5 of the paper, they already cover:
- Impact of descriptor embedding (E)
- Impact of task key (Kt) and loss (Lt)
- Impact of generators (Gt)
- Impact of class-wise key (Lc)
- Impact of auxiliary data
- Impact of inter-task loss
- Impact of soft task-id predictor

However, I notice two important missing ablations:

1. The impact of different language models for generating descriptors. The paper uses GPT-4 but doesn't evaluate how the choice of LLM affects performance. This is important since different LLMs may generate descriptors of varying quality.

2. The impact of the number of selected descriptors (k) in the top-k selection process. The paper fixes k=3 but doesn't evaluate how this hyperparameter affects the method's performance. This is crucial since k determines how many descriptors are used to generate prompts.

These ablations would help better understand the robustness and sensitivity of the method to these important design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### LLM Selection Ablation
- **Ablated Part**: Language model used for generating class descriptors
- **Action**: REPLACE
- **Replacement**: 
  - GPT-4
  - GPT-3
  - LLAMA
  - Gemini
- **Metrics**: FAA, CAA, FFM, CFM

### Top-k Selection Ablation
- **Ablated Part**: Number of selected descriptors (k) in top-k selection
- **Action**: REPLACE
- **Replacement**: 
  - k=1
  - k=2
  - k=4
  - k=5
- **Metrics**: FAA, CAA, FFM, CFM

</div>