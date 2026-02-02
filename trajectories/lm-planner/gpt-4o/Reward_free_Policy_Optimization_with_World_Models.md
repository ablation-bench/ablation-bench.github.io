<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Reward_free_Policy_Optimization_with_World_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Reward-free Policy Optimization with World Models" introduces a novel approach to reinforcement learning that eliminates the use of rewards as a learning signal. Instead, it focuses on goal-oriented policy learning using a backward world model to simulate trajectories and construct a directed graph for planning. The method is demonstrated in maze environments, showing its effectiveness in reaching goals without rewards.

The paper already includes several components that could be subject to ablation studies, such as the backward world model, the graph construction process, and the shortest path estimator (SPE). However, there are some aspects that could benefit from further investigation through ablation studies.

One potential area for ablation is the discretization of the state space. The paper mentions that discretization is crucial for constructing accurate graphs for planning. An ablation study could explore the impact of different discretization strategies or the absence of discretization on the method's performance.

Another area for ablation is the use of the shortest path estimator (SPE) in filtering simulations for policy learning. The SPE is used to evaluate whether a generated state-action pair should be used for policy learning. An ablation study could investigate the impact of removing the SPE or replacing it with alternative filtering mechanisms.

These ablation studies would help to better understand the contribution of these components to the overall performance of the RFPO method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Discretization
- **Ablated Part**: Discretization of the state space
- **Action**: REPLACE
- **Replacement**: 
  - No discretization
  - Different discretization strategies
- **Metrics**: Goal reachability, Graph construction accuracy

### Ablation of Shortest Path Estimator
- **Ablated Part**: Use of the shortest path estimator (SPE) for filtering simulations
- **Action**: REMOVE
- **Metrics**: Policy learning efficiency, Goal reachability

</div>