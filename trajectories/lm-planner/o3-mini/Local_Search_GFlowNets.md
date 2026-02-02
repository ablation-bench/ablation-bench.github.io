<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Local_Search_GFlowNets

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After carefully reviewing the method and the experimental sections, we note that the authors carried out several ablation studies on hyperparameters (such as the number of local search iterations I and candidate samples M), the filtering strategies (deterministic vs. stochastic), and the destructive/reconstructive step parameter K. However, one key component mentioned in the discussion as a limitation – the quality of the backward policy – has not been ablated. In LS-GFN, the backward policy is critical during the backtracking phase of the local search. Its quality can directly affect the acceptance rate and ultimately the performance in terms of average reward and the number of modes discovered. Therefore, it is important to study what happens when we replace this learned backward policy with a more exploratory variant (for example, by using a uniform random policy or an ϵ-greedy variant). 

A second potential ablation study that appears to be missing is the evaluation of applying the local search not only during training, but also at inference time. In the current experiments local search is only used for training (with samples at inference generated solely by the forward policy), to ensure fair comparison. However, it is interesting to assess whether incorporating a local search refinement step during inference (with either deterministic or stochastic filtering) would further enhance sample quality (e.g. higher top rewards and improved mode discovery) or simply incur extra computational cost without significant gains.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Exploratory Backward Policy
- **Ablated Part**: Backward policy used during the local search refinement step
- **Action**: REPLACE
- **Replacement**: 
  - Uniform Random Backtracking
  - ϵ-greedy Backtracking (epsilon=0.1)
  - ϵ-greedy Backtracking (epsilon=0.2)
- **Metrics**: Accuracy, Number of Modes, Top 100 Reward, Uniq. Fraction

### Ablation: Local Search at Inference
- **Ablated Part**: Exclusion of local search refinement during inference
- **Action**: ADD
- **Replacement**: 
  - Deterministic Filtering Local Search
  - Stochastic Filtering Local Search
- **Metrics**: Accuracy, Number of Modes, Top 100 Reward, Uniq. Fraction

</div>