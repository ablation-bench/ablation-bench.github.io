<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/A_Language_Agent_Approach_to_Formal_Theorem_Proving

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that while the authors conducted several ablation studies, there are still important components of COPRA that were not thoroughly investigated. Here's my reasoning for suggesting additional ablation studies:

1. The paper already includes ablations for:
- Using GPT-3.5 vs GPT-4 as the underlying LLM
- The impact of backtracking
- The impact of retrieval capabilities

2. However, two critical components that weren't ablated are:
- The failure dictionary (Bad) that tracks unproductive actions at each state
- The symbolic procedure that checks the partial order relationship between states (⊑)

These components are central to COPRA's design and directly impact its efficiency in finding proofs while minimizing unnecessary LLM queries. The failure dictionary helps avoid repeating failed tactics, while the partial order check prevents cycles and ensures progress in the proof search.

I suggest testing these components through two key ablation studies:

1. Remove the failure dictionary to understand how much it contributes to avoiding redundant LLM queries and improving proof search efficiency.

2. Remove the partial order check between states to assess its importance in preventing cyclic proofs and ensuring progress.

Both ablations should measure the same metrics used in the original paper to maintain consistency.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Failure Dictionary Ablation
- **Ablated Part**: The failure dictionary (Bad) that tracks unproductive actions at each state
- **Action**: REMOVE
- **Metrics**: number of theorems proved, average guidance steps in total, average guidance steps on failure, average guidance steps on pass, wall-clock time

### State Ordering Ablation
- **Ablated Part**: The symbolic procedure that checks partial order relationship between states (⊑)
- **Action**: REMOVE
- **Metrics**: number of theorems proved, average guidance steps in total, average guidance steps on failure, average guidance steps on pass, wall-clock time

</div>