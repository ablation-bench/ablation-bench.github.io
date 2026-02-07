<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Decoding_Game__On_Minimax_Optimality_of_Heuristic_Text_Generation_Strategies

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Decoding Game: On Minimax Optimality of Heuristic Text Generation Strategies" introduces the Decoding Game framework and derives an optimal strategy, which is approximated by the proposed Game sampling algorithm (Algorithm 1). The experimental section primarily focuses on comparing Game sampling with other decoding strategies and analyzing the impact of its hyperparameters (ϵ and τ).

While the paper explores the performance of Game sampling under different ϵ and τ values, it lacks ablation studies that dissect the specific components of the Game sampling algorithm itself, particularly those derived from the theoretical framework. Two key aspects derived from the theory are:
1.  The specific formula for calculating the sampling probabilities (qᵢ) within the truncated set (Theorem 4.4 and its first-order approximation in Corollary 4.5).
2.  The criterion used to determine the truncation threshold (Î) based on the game's objective and constraints (Theorem 4.4).

The paper states that standard truncation-normalization (where qᵢ ∝ p̂ᵢ) is a *first-order approximation* to the theoretically optimal q̃ (where qᵢ ∝ ŵᵢ = ϵ log(p̂ᵢ/(p̂ᵢ-ϵ))) for the log-likelihood case (τ=1). Algorithm 1 uses this first-order approximation when τ=1. A crucial missing ablation is to empirically compare the performance of Game sampling using this first-order approximation versus using the theoretically exact formula for qᵢ. This would directly assess the practical significance of the approximation.

Another important aspect is the theoretically derived criterion for setting the truncation threshold Î (S_I <= ϵ). The paper compares Game sampling (with its derived threshold) to other methods like Nucleus and Typical sampling (which use different threshold criteria), but it doesn't isolate the impact of the threshold criterion *within* the Game sampling framework. An ablation replacing the game-derived threshold criterion with common heuristic criteria (like fixed Top-k or cumulative probability) while keeping the rest of the Game sampling logic (e.g., using qᵢ ∝ p̂ᵢ) would reveal the importance of the specific threshold mechanism derived from the game theory.

Based on their direct link to the core theoretical contributions and the design of Algorithm 1, these two ablations are the most important missing ones. I rank the comparison of the probability weight formulas slightly higher as it directly tests the impact of the first-order approximation highlighted in the theoretical results.

The metrics used in the paper's experiments are Perplexity, Repetition frequency, and MAUVE score. These should be used for the proposed ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Game Sampling Probability Weights
- **Ablated Part**: Formula for calculating sampling probabilities within the truncated set for the log-likelihood objective (τ=1)
- **Action**: REPLACE
- **Replacement**: 
  - q_i ∝ p̂_i (First-order approximation)
  - q_i ∝ ϵ log(p̂_i / (p̂_i - ϵ)) (Theoretically exact form)
- **Metrics**: Perplexity, Repetition frequency, MAUVE score

### Game Sampling Truncation Threshold
- **Ablated Part**: Criterion used to determine the truncation index Î in Algorithm 1
- **Action**: REPLACE
- **Replacement**: 
  - Original criterion (S_I <= ϵ)
  - Fixed Top-k threshold
  - Nucleus-like cumulative probability threshold
- **Metrics**: Perplexity, Repetition frequency, MAUVE score

</div>