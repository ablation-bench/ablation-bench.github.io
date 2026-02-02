<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Navigation_with_QPHIL__Offline_Goal_Conditioned_RL_in_a_Learned_Discretized_Space

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One key component of QPHIL is its transformer‐based high-level plan generator, which is conditioned on the full sequence of previously visited tokens. However, the paper only uses the full-history conditioning without comparing a simpler variant. An important missing ablation is to replace this full-history conditioning with a Markovian setup (i.e. conditioning only on the current state’s token) to test whether the extra context improves the generation of effective landmark sequences. In addition, although the transformer is chosen for its ability to capture long-range dependencies, it is unclear if this architectural choice is essential for the planning module. Therefore, a second crucial missing ablation would be to replace the transformer with simpler recurrent architectures (e.g., LSTM or GRU) and compare their performance on navigation tasks. Both ablations would measure improvements in navigation success rate, subgoal completion, and planning consistency.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Full-History vs. Markov Planner
- **Ablated Part**: Transformer-based plan generator’s conditioning mechanism, comparing full-history conditioning against a simplified Markov assumption using only the current token.
- **Action**: REPLACE
- **Replacement**: 
  - Full-history conditioning
  - Single-token (Markov) conditioning
- **Metrics**: Success Rate, Subgoal Completion Rate, Trajectory Stitching Accuracy

### Ablation: RNN-based Planner
- **Ablated Part**: High-level subgoal planning architecture; specifically, the use of a transformer for sequence generation.
- **Action**: REPLACE
- **Replacement**: 
  - LSTM-based planner
  - GRU-based planner
- **Metrics**: Success Rate, Subgoal Completion Rate, Planning Consistency

</div>