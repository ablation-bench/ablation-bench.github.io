<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Align_Your_Intents__Offline_Imitation_Learning_via_Optimal_Transport

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user requested up to two missing ablation studies for the paper "Align Your Intents: Offline Imitation Learning via Optimal Transport (AILOT)".

I first analyzed the paper to understand the core components of the AILOT method and the ablation studies already presented. AILOT's key ideas are:
1.  Learning a state representation ("intents" via ICVF pretraining) that preserves temporal distances.
2.  Defining an intrinsic reward using Optimal Transport distance between expert and agent trajectories in this intent space, using a specific cost function (Equation 10) that includes both current and future state intent distances.

The paper includes ablations on:
*   Number of expert trajectories (Appendix C).
*   Reward scaling hyperparameters (Appendix E).
*   Empirical verification of the temporal distance property of the intent space (Figure 3).
*   Comparison with OTR (which uses raw states and a different cost function) and a note that using AILOT's cost function in OTR yields minor improvements (Appendix C).

Based on this, two crucial missing ablations stand out:

1.  **Ablating the use of the learned intent space:** The paper claims the intent space is vital because it's metric-aware and preserves temporal distances, making OT effective. While they compare to OTR (which uses raw states), a direct ablation *within the AILOT framework* comparing the use of the learned intent `ψ(s)` versus the raw state `s` in the OT cost function (Equation 10) is missing. This would isolate the contribution of the learned representation itself.
2.  **Ablating the temporal term in the cost function:** The cost function (Equation 10) includes a term measuring the distance between future state intents (`||ψ(s_{min{i+k, Ta}}^a) - ψ(s_{min{j+k, Te}}^e)||^2`). The paper states this term is "necessary for an ordered comparison". Removing this term would test its importance and whether matching only current state intents is sufficient.

These two ablations directly test the impact of the learned representation and the specific structure of the cost function designed for it, which are central to AILOT's novelty and performance claims. They are more fundamental than ablating hyperparameters or the downstream RL algorithm.

The metrics used throughout the paper are normalized scores (mean ± standard deviation) on D4RL benchmarks (MuJoCo, AntMaze, Adroit), which should be used for these ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Raw State vs. Intent Space Cost
- **Ablated Part**: Use of learned intent space (ψ) in the Optimal Transport cost function
- **Action**: REPLACE
- **Replacement**: 
  - Raw state (s)
- **Metrics**: Normalized Score (mean ± std)

### Cost Function Temporal Term
- **Ablated Part**: Second term (future state intent distance) in the Optimal Transport cost function (Equation 10)
- **Action**: REMOVE
- **Metrics**: Normalized Score (mean ± std)

</div>