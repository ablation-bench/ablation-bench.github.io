<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/sapg

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "SAPG: Split and Aggregate Policy Gradients" proposes a new on-policy reinforcement learning algorithm designed to effectively utilize massively parallel environments. The core idea is to split the total environments among multiple policies and aggregate the data collected by these policies using off-policy updates. The method introduces several key components:
1.  **Splitting:** Dividing environments among $M$ policies.
2.  **Multiple Policies:** Training $M$ distinct policies.
3.  **Parameterization:** Using a shared backbone with learned local parameters ($\phi_j$) for each policy.
4.  **Aggregation Scheme:** Employing a "Leader-follower" structure where a leader policy aggregates data from follower policies via importance sampling. A "Symmetric" scheme is also mentioned.
5.  **Off-policy Update:** Using importance sampling and specific critic targets for off-policy data.
6.  **Diversity Encouragement:** Using learned latents and differential entropy regularization for followers.

To understand which of these components contribute most to SAPG's performance, we propose a set of ablation studies. We prioritize ablations that test the core "Split and Aggregate" mechanism and the specific choices made within it.

1.  **Ablating Aggregation:** The most fundamental part of SAPG is the aggregation of data from multiple policies. Removing this (i.e., having policies train only on their own data, like independent PPO runs) directly tests the value of the "Aggregate" step. This is the highest priority ablation.
2.  **Ablating the Aggregation Scheme:** SAPG proposes a specific "Leader-follower" scheme. Comparing this to the alternative "Symmetric" scheme mentioned in the paper will show if the asymmetric aggregation is crucial or if any form of aggregation is sufficient.
3.  **Ablating Policy Parameterization:** The paper uses a shared backbone with learned local latents to parameterize the multiple policies. Ablating the learned latents tests if this specific mechanism for encouraging diversity and specialization among policies is necessary, or if a simpler shared network structure would suffice.
4.  **Ablating Explicit Diversity:** SAPG uses differential entropy regularization on follower policies to explicitly encourage diverse exploration. Ablating this tests if the splitting, aggregation, and learned latents are sufficient to maintain diversity, or if this explicit regularization is important.
5.  **Ablating the Number of Splits:** The performance might be sensitive to the number of policies ($M$) used to split the environments. Varying $M$ tests the impact of the granularity of the "Split" step.

The primary metrics used in the paper and standard for RL evaluation are average reward (especially asymptotic performance) and the learning curve (performance over environment steps). These will be used for the ablation studies.

Based on this reasoning, the following 5 ablation studies are proposed, ranked by importance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### SAPG-NoAggregate
- **Ablated Part**: Off-policy data aggregation from follower policies to the leader
- **Action**: REMOVE
- **Metrics**: Average Reward, Learning Curve

### SAPG-SymmetricAggregate
- **Ablated Part**: Leader-follower aggregation scheme
- **Action**: REPLACE
- **Replacement**: 
  - Symmetric aggregation scheme (each policy aggregates from all others)
- **Metrics**: Average Reward, Learning Curve

### SAPG-NoLatents
- **Ablated Part**: Learned local parameters (phi_j) for policy conditioning
- **Action**: REMOVE
- **Metrics**: Average Reward, Learning Curve

### SAPG-NoEntropy
- **Ablated Part**: Differential entropy regularization for follower policies
- **Action**: REMOVE
- **Metrics**: Average Reward, Learning Curve

### SAPG-VaryM
- **Ablated Part**: Number of policies (M)
- **Action**: REPLACE
- **Replacement**: 
  - M=2
  - M=4
  - M=16
- **Metrics**: Average Reward, Learning Curve

</div>