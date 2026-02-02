<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Evolving_Alignment_via_Asymmetric_Self_Play

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Let me analyze the key components of the EVA method and existing ablations:

1. The paper already includes ablations on:
- Different informativeness metrics (reward variance, mean, advantage)
- Different evolving methods (EvolInstruct, EvolQuality, EvolComplexity, SelfInstruct)
- Different reward models (pointwise vs pairwise)
- Different training schedules (incremental vs scratch)

2. Key components that lack ablation analysis:

a) The buffer mixing ratio: The paper mentions mixing evolved prompts with a buffer of original prompts but doesn't analyze the impact of this ratio. This is important since it affects the balance between exploration and exploitation.

b) The number of responses sampled per prompt: The paper uses 6 responses per prompt for calculating informativeness but doesn't justify this choice. This parameter directly affects the quality of the informativeness estimate.

These components are critical for the method's performance and deserve dedicated ablation studies.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Buffer Mixing Ratio Ablation
- **Ablated Part**: The ratio of evolved prompts vs original prompts in the training set
- **Action**: REPLACE
- **Replacement**: 
  - 0% buffer (all evolved)
  - 20% buffer (default)
  - 50% buffer
  - 80% buffer
- **Metrics**: win rate on Arena-Hard, average score on MT-Bench, win rate on AlpacaEval 2.0

### Response Sampling Size Ablation
- **Ablated Part**: Number of responses sampled per prompt for informativeness calculation
- **Action**: REPLACE
- **Replacement**: 
  - 2 responses
  - 4 responses
  - 6 responses (default)
  - 8 responses
  - 10 responses
- **Metrics**: win rate on Arena-Hard, average score on MT-Bench, win rate on AlpacaEval 2.0

</div>