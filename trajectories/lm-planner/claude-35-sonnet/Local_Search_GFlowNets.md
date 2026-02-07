<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Local_Search_GFlowNets

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

First, let me analyze the existing ablations in the paper:
1. The paper includes ablations on filtering strategies (deterministic vs stochastic) in Section B.2
2. There are ablations on the number of revision steps (I) and batch size (M) in Section B.3
3. They study different K values (number of destruction/reconstruction steps) in Section B.5

Looking at the core components of the method:
1. The main novelty is the local search mechanism which consists of:
   - Backtracking using backward policy
   - Reconstruction using forward policy
   - Filtering strategy
2. The paper thoroughly ablates the filtering strategy and K parameter, but doesn't investigate alternatives to the backtracking/reconstruction approach.

Two important missing ablations are:

1. The choice of using backward policy for backtracking - they could compare it against random backtracking or other strategies
2. The choice of using the same forward policy for both initial sampling and reconstruction - they could use different policies or parameters

These ablations would help understand if the specific policy choices are important for the method's success.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Backtracking Strategy Ablation
- **Ablated Part**: backward policy used for backtracking
- **Action**: REPLACE
- **Replacement**: 
  - random backtracking
  - uniform policy
  - epsilon-greedy backward policy
- **Metrics**: accuracy, number of modes, top 100 reward, unique fraction

### Reconstruction Policy Ablation
- **Ablated Part**: forward policy used for reconstruction
- **Action**: REPLACE
- **Replacement**: 
  - separate reconstruction policy
  - epsilon-greedy forward policy
  - temperature-scaled forward policy
- **Metrics**: accuracy, number of modes, top 100 reward, unique fraction

</div>