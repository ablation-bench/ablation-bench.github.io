<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/On_Policy_Policy_Gradient_Reinforcement_Learning_Without_On_Policy_Sampling

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "On-Policy Policy Gradient Reinforcement Learning Without On-Policy Sampling" introduces PROPS, a method that uses an adaptive, off-policy behavior policy to collect data that reduces sampling error in a replay buffer, which is then used for on-policy policy gradient updates (specifically PPO). The core idea is to achieve on-policy *data* without requiring on-policy *sampling*.

The method involves several key components:
1.  Maintaining a replay buffer `D` of historic data.
2.  Using a separate behavior policy `πϕ` for data collection, distinct from the target policy `πθ`.
3.  Periodically updating the behavior policy `πϕ` (Algorithm 2) to make the data distribution in `D` closer to the current target policy `πθ` distribution. This update uses a clipped objective (LCLIP) and a KL regularization term, stopping when the KL divergence between `πθ` and `πϕ` exceeds a threshold `δPROPS`.
4.  Using the data in `D` to update the target policy `πθ` (Algorithm 1, Line 11) using a standard on-policy algorithm like PPO.

The paper already includes several important ablation studies:
*   Comparison to vanilla PPO (on-policy sampling, no buffer) and PPO-BUFFER (on-policy sampling, with buffer, essentially Algorithm 1 with `πϕ = πθ` and no Algorithm 2 update). This demonstrates the benefit of the PROPS approach over naive data reuse and standard on-policy sampling.
*   Ablations of the buffer size `b` (Appendix D).
*   Ablations of the clipping coefficient `ϵPROPS` (by setting it to infinity) and the regularization coefficient `λ` (by setting it to zero) in the PROPS update objective (Appendix C and D). These show the importance of these specific terms in the PROPS update for reducing sampling error and improving data efficiency.

Based on the method description and existing ablations, I identify two important missing ablation studies:

1.  **Frequency of Behavior Policy Updates:** Algorithm 1 updates the behavior policy `πϕ` every `m` steps of data collection, while the target policy `πθ` is updated every `n` steps, where `n > m`. This means the behavior policy is updated `n/m` times for every target policy update. The paper sweeps over different values of `m` and `n` during hyperparameter tuning (Table 2) and shows some results for different `m` values in Figure 17. However, an explicit ablation study varying the *ratio* `n/m` (i.e., the frequency of behavior policy updates relative to target policy updates) while keeping other factors (like total data per target update) controlled would clearly show how often the adaptive correction is needed and its impact on performance and sampling error. This is a fundamental structural aspect of Algorithm 1 that hasn't been isolated.

2.  **KL Divergence Stopping Criterion:** The PROPS update (Algorithm 2) includes a stopping condition based on the KL divergence between the target policy `πθ` and the behavior policy `πϕ` (DKL(πθ||πϕ) > δPROPS). This is a key mechanism to prevent the behavior policy from diverging too much from the target policy during its update steps. The paper sweeps over `δPROPS` (Table 2) but does not explicitly show an ablation where this stopping criterion is *removed* entirely, forcing the Algorithm 2 update to run for a fixed number of epochs (`n_epoch`) regardless of the KL divergence. This ablation would demonstrate the importance of this dynamic stopping mechanism for the stability and effectiveness of the PROPS update during RL training.

These two ablations are important because they investigate core mechanisms of the PROPS algorithm's control flow (how often the behavior policy is updated) and its update process (how the behavior policy update is terminated), which are distinct from the specific terms in the update objective (clipping, regularization) that were already ablated. They would provide further insight into *why* PROPS works and which aspects are critical.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Behavior Update Frequency
- **Ablated Part**: Frequency of behavior policy updates relative to target policy updates (ratio n/m)
- **Action**: REPLACE
- **Replacement**: 
  - n/m = 1
  - n/m = 2
  - n/m = 4
  - n/m = 8
  - n/m = 16
- **Metrics**: IQM return, Performance profile, DKL(πD||πθ)

### KL Stopping Criterion
- **Ablated Part**: KL divergence stopping criterion in the PROPS behavior policy update (Algorithm 2, Line 9-10)
- **Action**: REMOVE
- **Metrics**: IQM return, Performance profile, DKL(πD||πθ)

</div>