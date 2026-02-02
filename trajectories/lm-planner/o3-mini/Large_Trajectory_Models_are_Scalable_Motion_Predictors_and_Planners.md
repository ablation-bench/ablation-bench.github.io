<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Large_Trajectory_Models_are_Scalable_Motion_Predictors_and_Planners

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The STR paper already ablates the ordering of Key Points (forward versus backward) and the use of diffusion vs. MLP decoders for Key Points. However, two important aspects remain unexplored. First, the overall order of components in the unified sequence (i.e. how Context, Proposal, Key Points, and Future States are concatenated) might influence the model’s ability to align heterogeneous signals. Testing alternative ordering strategies (for example switching the positions of Proposal and Key Points) could shed light on the sensitivity of the sequence modeling process to token order. Second, the paper fixes the number of Key Points at 5 without evaluating whether this is optimal for long-term reasoning and guidance. Varying the number of Key Points (e.g., 3, 5, or 7) would help determine if different granularities of high-level guidance lead to better performance, measured in terms of displacement errors, miss rate and overall open-loop score. These two ablations promise to provide deeper insights into the design choices for the STR method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Sequence Ordering Ablation
- **Ablated Part**: The unified sequence structure combining Context, Proposal, Key Points, and Future States
- **Action**: REPLACE
- **Replacement**: 
  - [Context, Proposal, Key Points, Future States]
  - [Context, Key Points, Proposal, Future States]
  - [Proposal, Context, Key Points, Future States]
- **Metrics**: 8sADE, 3sFDE, 5sFDE, 8sFDE, MR, OLS

### Key Points Count Ablation
- **Ablated Part**: The set number of Key Points used as intermediate high-level guidance in the sequence
- **Action**: REPLACE
- **Replacement**: 
  - 3
  - 5
  - 7
- **Metrics**: 8sADE, 3sFDE, 5sFDE, 8sFDE, MR, OLS

</div>