<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Knowledge_Accumulating_Contrastive_Prompt_for_Continual_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a novel prompt-based continual learning method that accumulates knowledge in a single prompt using contrastive learning. The core technical contributions are the use of a single prompt (avoiding prompt pools and task prediction) and two contrastive loss terms, `L_ctr` and `L_prev`, designed to increase the dependency between features derived from the current and previous prompts/encoders. The overall loss is `L = L_cls + λ_ctr L_ctr + λ_prev L_prev`.

The paper includes several ablation studies and analyses:
1.  Ablation on `λ_prev` (Table 5), showing the impact of the `L_prev` term on performance and the plasticity-stability tradeoff. This effectively ablates the contribution of `L_prev`.
2.  Comparison with other contrastive losses (Table 7), showing that the chosen SimSiam-like approach performs best among tested alternatives.
3.  Ablation on prompt length (Table 8), demonstrating robustness to this hyperparameter.
4.  Analysis of feature space alignment (Figure 7, Figure 8), providing insights into *how* the method works, including the effect of `L_ctr` and `L_prev` on eigenvector similarity, but not quantifying their contribution to the final performance metrics (Average Accuracy, Forgetting).
5.  Comparison of computational costs and limitations of prompt pools (Table 3, Table 4), highlighting the advantages of the single-prompt approach compared to previous methods like L2P and DualPrompt.

Based on this analysis, two important missing ablation studies stand out:

1.  **Ablation of `L_ctr`:** While the paper ablates `L_prev` and analyzes the feature space with `L_ctr` alone, it does not quantitatively assess the contribution of the `L_ctr` loss term to the final Average Accuracy and Forgetting metrics. `L_ctr` is a key component of the proposed contrastive learning framework, directly pulling features from the current and previous prompts using the base model. Ablating this term (by setting `λ_ctr=0` for tasks where it's applied, i.e., tasks >= 2 according to Algorithm 1) would clearly demonstrate its necessity and impact on mitigating catastrophic forgetting and maintaining accuracy.

2.  **Ablation of Prompt Accumulation Mechanism:** The paper's central claim is accumulating knowledge in a single prompt. The pseudo-code (Algorithm 1) shows that after training on task `t`, the previous prompt `p^e` is simply replaced by the newly learned prompt `p`. This is the specific mechanism of accumulation. An ablation study exploring alternative ways to update `p^e` (e.g., averaging or interpolating the old `p^e` with the new `p`) would investigate whether this simple replacement is optimal or if a smoother accumulation strategy could yield better results. This directly tests the effectiveness of the proposed accumulation method.

These two ablations are crucial for understanding the individual contributions of the novel loss terms and the specific knowledge accumulation strategy, which are the core technical contributions of the paper. They would provide stronger evidence for the design choices made. I will prioritize the ablation of `L_ctr` as it directly tests one of the two main contrastive loss components.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of L_ctr
- **Ablated Part**: The contrastive loss term L_ctr between current and previous prompt features (f(X, p^t) and f(X, p^{t-1})).
- **Action**: REMOVE
- **Metrics**: Average Accuracy, Forgetting

### Ablation of Prompt Update Rule
- **Ablated Part**: The mechanism for updating the previous prompt (p^e) after training on a task.
- **Action**: REPLACE
- **Replacement**: 
  - p^e = (1-α) p^e + α p with α=0.25
  - p^e = (1-α) p^e + α p with α=0.5
  - p^e = (1-α) p^e + α p with α=0.75
- **Metrics**: Average Accuracy, Forgetting

</div>