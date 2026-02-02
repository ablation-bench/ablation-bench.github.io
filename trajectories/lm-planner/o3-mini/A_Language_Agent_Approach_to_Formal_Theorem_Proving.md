<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/A_Language_Agent_Approach_to_Formal_Theorem_Proving

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two new ablation experiments that isolate key components responsible for COPRA’s performance. Although the paper already considers variations such as using GPT‑3.5 instead of GPT‑4, disabling retrieval, or even removing backtracking, it does not explicitly measure the contribution of the feedback loop and historical context maintained in the LLM prompts.

The first proposed ablation removes the execution feedback from the prompt serialization protocol. In COPRA, after each tactic is executed in the proof environment, its execution feedback (e.g., error messages) is incorporated into the next LLM prompt. This “feedback loop” is designed to reduce hallucinations and avoid repeating wrong steps. Testing COPRA without this execution feedback will show whether this component is essential in guiding the search effectively, as measured by metrics such as percentage of theorems proved, average guidance steps (total, on failure, and on success), or the wall-clock time per proof.

The second proposed ablation targets the history tracking feature. COPRA maintains a state stack and failure dictionary to include past states, tactics, and their outcomes in the prompt constructed for the LLM. Removing this historical context will demonstrate whether the additional context provided by the past execution history (which helps in avoiding cycles and repeated mistakes) significantly benefits the proof search, as reflected in the same performance and efficiency metrics. These two ablations would be ranked by importance with the execution feedback removal being the highest priority because it distinguishes COPRA’s interactive, environment-aware approach from one-shot prompting.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Execution Feedback
- **Ablated Part**: Execution feedback component of the prompt serialization protocol that incorporates the proof environment's execution result (error messages or success indicators) into the LLM prompt
- **Action**: REMOVE
- **Metrics**: %_proved, avg_guidance_steps_total, avg_guidance_steps_on_failure, avg_guidance_steps_on_success, avg_wall_clock_time_per_proof

### Ablation: Remove History Context
- **Ablated Part**: Historical context in the prompt, including the state stack and failure dictionary (Bad) used to provide context from prior proof states
- **Action**: REMOVE
- **Metrics**: %_proved, avg_guidance_steps_total, avg_guidance_steps_on_failure, avg_guidance_steps_on_success

</div>