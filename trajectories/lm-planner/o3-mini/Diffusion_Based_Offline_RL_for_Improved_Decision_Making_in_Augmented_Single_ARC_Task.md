<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Diffusion_Based_Offline_RL_for_Improved_Decision_Making_in_Augmented_Single_ARC_Task

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Our first proposed ablation is to investigate the impact of the training data composition by varying the ratio of non‐optimal trajectories to gold-standard trajectories in SOLAR. Although the paper uses a mixture (approximately 10% optimal rather than non-optimal), it does not report results isolating the influence of non-optimal data. Evaluating models trained on exclusively gold-standard data versus mixtures with different ratios (e.g., 100% gold-standard versus 80%-20% or even 50%-50% splits) can provide insight into how the diversity of synthesized trajectories contributes to the reasoning ability and decision-making performance—particularly in terms of reaching the answer state and executing the Submit operation appropriately.
Our second proposed ablation targets the discount factor used in the Q-learning component. The paper sets the discount factor at 0.5, a design choice that may influence the Q-function’s ability to balance immediate actions with long-term objectives. By replacing the current discount factor with a range of values (such as 0.3, 0.5, and 0.9), we can assess how sensitive the performance metrics (e.g., accuracy in reaching the answer state and correct submission) are to this hyperparameter. This ablation directly addresses the observation that, in some cases, the agent reaches the answer state but fails to submit, suggesting that adjusting the discount factor could help better align the Q-values with the overall task objective.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Impact of Non-Optimal Trajectory Ratio
- **Ablated Part**: Composition of SOLAR training dataset, specifically the ratio between gold-standard trajectories and non-optimal trajectories
- **Action**: REPLACE
- **Replacement**: 
  - 100% Gold-Standard
  - 80%-20% Gold vs Non-Optimal
  - 50%-50% Gold vs Non-Optimal
- **Metrics**: Answer State Reach Accuracy, Submit Operation Accuracy, Overall Task Success Rate

### Ablation: Effect of Q-function Discount Factor
- **Ablated Part**: Hyperparameter setting of discount factor in the Q-learning component of LDCQ
- **Action**: REPLACE
- **Replacement**: 
  - 0.3
  - 0.5
  - 0.9
- **Metrics**: Answer State Reach Accuracy, Submit Operation Accuracy, Q-value Alignment (e.g., consistency between predicted actions and goal state)

</div>