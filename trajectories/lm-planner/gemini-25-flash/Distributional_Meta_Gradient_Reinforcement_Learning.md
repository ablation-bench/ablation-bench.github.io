<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Distributional_Meta_Gradient_Reinforcement_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Distributional Meta-Gradient Reinforcement Learning" proposes DrMG, a novel algorithm that combines meta-gradient reinforcement learning with distributional value estimation, specifically using quantile regression. The core idea is to learn an adaptive distributional return target using meta-gradients, moving beyond the traditional expected return.

The paper presents several ablation studies in Section 5.3 to understand the contribution of different components:
1.  **Adaptive vs. non-adaptive distributional return:** Compares DrMG (adaptive) with QR (non-adaptive, no meta-gradient) and DrMG(η1) (meta-learns only loss weights, fixed return parameters). This shows the benefit of meta-learning the return parameters (η0 = {λ, γ, α}).
2.  **λ-distributional return vs. n-step distributional return:** Compares DrMG (λ-return) with DrMG+n-step (using n=3 and n=5). This demonstrates the superiority of the λ-return formulation in this context.
3.  **Vector hyperparameters η vs. scalar hyperparameters η¯:** Compares DrMG with quantile-specific (vector) hyperparameters against a version with scalar hyperparameters shared across quantiles. This highlights the benefit of quantile-specific adaptation.

While these ablations cover important aspects, there are still key design choices and hyperparameters whose impact is not fully explored. Based on the method description and the existing ablations, two important missing ablation studies are:

1.  **The Number of Quantiles (N):** The distributional approach approximates the value distribution using N quantiles. The choice of N is fundamental to any distributional RL method, influencing the granularity of the distribution representation, computational cost, and potentially performance. The paper mentions N (or nZ) as the dimension of quantiles but does not provide an ablation study varying this parameter to show its effect on DrMG's performance.
2.  **The Specific Set of Meta-Learned Parameters:** DrMG meta-learns a set of hyperparameters η = {λ, γ, α, wH, wπ, wZ}. Ablation (i) shows that meta-learning η0 = {λ, γ, α} is important compared to fixing them. Ablation (iii) shows that making η vector is beneficial. However, the individual contribution or necessity of *each* component within the full set η is not fully clear. For instance, is meta-learning the v-trace parameter α, or the policy/entropy loss weights (wH, wπ), as important as meta-learning the core distributional return parameters (λ, γ, wZ)? An ablation comparing the full set η with reduced sets focusing on the core distributional parameters would provide valuable insight into which aspects of the meta-learned objective are most critical for DrMG's success.

These two ablations would provide a more comprehensive understanding of DrMG's performance drivers, specifically regarding the distributional representation's granularity and the specific components of the meta-learned objective. The metrics used in the paper, such as Median Human Normalized Score and learning curves showing performance over training frames, would be appropriate for these studies.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Number of Quantiles
- **Ablated Part**: Number of quantiles (N) used for distributional value representation.
- **Action**: REPLACE
- **Replacement**: 
  - 10
  - 51
  - 200
- **Metrics**: Median Human Normalized Score, Learning Curves (Human Normalized Score)

### Ablation: Set of Meta-Learned Parameters
- **Ablated Part**: Specific hyperparameters included in the meta-learned set η.
- **Action**: REPLACE
- **Replacement**: 
  - {λ, γ, wZ} (vectorial)
  - {λ, γ, α, wZ} (vectorial)
  - {λ, γ, α, wH, wπ, wZ} (vectorial, full set)
- **Metrics**: Median Human Normalized Score, Learning Curves (Human Normalized Score)

</div>