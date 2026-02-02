<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/A_General_Framework_for_Off_Policy_Learning_with_Partially_Observed_Reward

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "A General Framework for Off-Policy Learning with Partially-Observed Reward" proposes HyPeR, a method for off-policy learning in contextual bandits with partially-observed target rewards, which leverages more densely observed secondary rewards. The core of HyPeR lies in its policy gradient estimator (Eq. 11), which is a weighted sum of an estimator for the target reward gradient (Eq. 10) and an estimator for the secondary reward gradient. The paper also introduces a data-driven tuning mechanism for the weight (γ) in this sum.

The paper conducts several experiments comparing HyPeR variants (HyPeR(γ=β), HyPeR(γ=0), HyPeR(Tuned γˆ ∗ )) against baselines like r-DR (using only observed target rewards) and s-DR (using only secondary rewards). These comparisons demonstrate the overall effectiveness of HyPeR and the benefit of strategically tuning the weight γ. The paper also explores the impact of varying observation probability, data size, target-secondary reward correlation, noise levels, and action space size. An ablation study on the bootstrapping procedure for tuning γ is also presented.

While the paper effectively shows that combining target and secondary rewards via HyPeR is beneficial, and that the tuning mechanism works, there are a couple of important aspects that could be further investigated through ablation studies to better understand HyPeR's performance attribution:

1.  **The contribution of specific secondary reward types:** The real-world experiment uses a multi-dimensional secondary reward (4 dimensions in KuaiRec). The paper shows that using these secondary rewards is better than not using them (comparing HyPeR to r-DR), and that using only secondary rewards (s-DR) is often insufficient due to misalignment. However, it's unclear which of the specific secondary reward dimensions contribute most to HyPeR's performance. An ablation study varying the *subset* of secondary rewards used would shed light on their individual and combined utility. This is particularly relevant in real-world scenarios where different types of secondary signals might be available with varying degrees of correlation to the target and varying observation densities (though the paper assumes secondary rewards are fully observed).

2.  **The specific structure of the target reward gradient estimator (Eq. 10):** HyPeR's target reward gradient estimator (∇θVˆ r) is a key component, especially when the target reward objective is prioritized (small β or γ). This estimator is more complex than a standard r-DR estimator (Eq. 5). It incorporates terms involving both qˆ(x,a) and qˆ(x,a,s). The paper shows HyPeR(γ=0) (which uses this estimator) outperforms r-DR, suggesting the specific way HyPeR leverages secondary rewards for the target gradient is effective. However, it doesn't compare this specific structure against alternative ways of incorporating secondary rewards into a target gradient estimator. For instance, a simpler approach might be to use a standard DR estimator but condition the outcome model (q-function) on the secondary rewards (qˆ(x,a,s)). Ablating the specific structure of Eq. 10 by replacing it with such a simpler, yet still secondary-reward-aware, target gradient estimator would help understand if the complexity of Eq. 10 is necessary for its performance gains.

Based on this analysis, the two most important missing ablation studies are the ones exploring the specific secondary reward dimensions and the specific structure of the target reward gradient estimator.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Secondary Reward Dimensions Ablation
- **Ablated Part**: Specific dimensions of multi-dimensional secondary rewards used in HyPeR.
- **Action**: REPLACE
- **Replacement**: 
  - Only s1
  - Only s2
  - Only s3
  - Only s4
  - s1+s2
  - s1+s2+s3+s4 (current)
  - Other relevant subsets
- **Metrics**: Relative Combined policy value, Relative Target policy value, Relative Secondary policy value

### Alternative Target Gradient Estimator
- **Ablated Part**: The specific structure of the target reward policy gradient estimator (Eq. 10) used as the first term in HyPeR (Eq. 11).
- **Action**: REPLACE
- **Replacement**: 
  - Replace Eq. 10 with a Doubly Robust estimator that conditions the outcome model on secondary rewards: (o_i / p(o_i|x_i)) * w(x_i, a_i) * (r_i - q_hat(x_i, a_i, s_i)) * g_theta(x_i, a_i) + E_{pi_theta(a|x_i)}[q_hat(x_i, a, s_i) * g_theta(x_i, a)] (summed over n data points and divided by n)
- **Metrics**: Relative Combined policy value, Relative Target policy value, Relative Secondary policy value

</div>