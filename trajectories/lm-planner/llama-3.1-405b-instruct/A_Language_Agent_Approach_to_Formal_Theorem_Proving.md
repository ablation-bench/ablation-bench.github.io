<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/A_Language_Agent_Approach_to_Formal_Theorem_Proving

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents a language-agent approach to formal theorem-proving, called COPRA, which uses a high-capacity, black-box LLM (GPT-4) as part of a policy for a stateful backtracking search. The approach is evaluated on the miniF2F benchmark for Lean and a set of Coq tasks from the Compcert project, and it is shown to be significantly better than one-shot invocations of GPT-4 and state-of-the-art models fine-tuned on proof data.

To further evaluate the effectiveness of COPRA, we suggest two missing ablation studies:

1. **Ablation of the LLM model**: The current approach uses GPT-4 as the underlying LLM. It would be interesting to see how the performance of COPRA changes when using other LLM models, such as GPT-3.5 or CodeLlama. This ablation study would help to understand the impact of the LLM model on the overall performance of COPRA.
2. **Ablation of the backtracking search**: The current approach uses a stateful backtracking search. It would be interesting to see how the performance of COPRA changes when using a different search strategy, such as a breadth-first search or a depth-first search without backtracking. This ablation study would help to understand the impact of the search strategy on the overall performance of COPRA.

These ablation studies would provide valuable insights into the effectiveness of COPRA and help to identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of LLM model
- **Ablated Part**: LLM model
- **Action**: REPLACE
- **Replacement**: 
  - GPT-3.5
  - CodeLlama
- **Metrics**: pass@k-guidance-steps, wall-clock time

### Ablation of backtracking search
- **Ablated Part**: backtracking search
- **Action**: REPLACE
- **Replacement**: 
  - breadth-first search
  - depth-first search without backtracking
- **Metrics**: pass@k-guidance-steps, wall-clock time

</div>