<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/A_General_Framework_for_Off_Policy_Learning_with_Partially_Observed_Reward

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes HyPeR, a method for off-policy learning that leverages both partially-observed target rewards and fully-observed secondary rewards. The key components of the method are:

1. A new policy gradient estimator that combines target and secondary rewards (Eq. 10)
2. A tunable parameter γ that controls the mixture ratio between target and secondary rewards (Eq. 11)
3. A data-driven tuning procedure for γ using bootstrapping (Eq. 14)

Looking at the existing ablations in the paper:
- They compare HyPeR with different γ values (γ=0, γ=β, tuned γ)
- They analyze performance with varying observation probabilities, data sizes, reward correlations
- They test with different noise levels in rewards and estimated observation probabilities

However, I notice two important missing ablations:

1. The bootstrapping procedure in the γ tuning process is a key design choice but its specific impact is not fully isolated. While they briefly compare with/without replacement sampling in Table 2, a dedicated ablation would better quantify its importance.

2. The paper uses a specific form of combining target and secondary rewards in Eq. 10, but does not ablate this design choice against alternative combination strategies. This would help validate their specific formulation.

I'll suggest these two ablations in order of importance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Bootstrapping Ablation
- **Ablated Part**: bootstrapping procedure in gamma tuning
- **Action**: REPLACE
- **Replacement**: 
  - without replacement sampling
  - random split validation
  - k-fold cross validation
- **Metrics**: combined policy value, target policy value, secondary policy value

### Reward Combination Ablation
- **Ablated Part**: reward combination strategy in policy gradient estimation
- **Action**: REPLACE
- **Replacement**: 
  - weighted sum of gradients
  - product of gradients
  - adaptive gating mechanism
- **Metrics**: combined policy value, target policy value, secondary policy value

</div>