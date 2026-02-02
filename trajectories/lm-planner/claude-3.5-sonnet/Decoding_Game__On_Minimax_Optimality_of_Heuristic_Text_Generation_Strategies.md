<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Decoding_Game__On_Minimax_Optimality_of_Heuristic_Text_Generation_Strategies

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a theoretical framework called "Decoding Game" that explains why heuristic sampling strategies like Top-k and Nucleus sampling work well in practice. The key components of their method are:

1. A two-player zero-sum game between Strategist (who generates text) and Nature (who adversarially distorts the true distribution)
2. The use of Total Variation (TV) distance to define the neighborhood of possible distributions
3. A first-order approximation that leads to truncation-normalization sampling strategies
4. A temperature parameter τ that controls the sampling distribution

Looking at the existing experiments in Section 5, they evaluate:
- Different values of ϵ (distance budget parameter)
- Different values of τ (temperature parameter)
- Comparison with other sampling methods
- Metrics: perplexity, repetition frequency, and MAUVE score

However, I notice two important missing ablation studies:

1. The choice of TV distance metric is crucial but not justified experimentally. They should compare it with other distance metrics like KL-divergence which is commonly used in language modeling.

2. The paper assumes an adversarial Nature player but doesn't explore how different adversarial strategies affect the results. They could compare their minimax formulation with simpler non-adversarial approaches.

These ablations would help validate key modeling choices in their theoretical framework.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Distance Metric Ablation
- **Ablated Part**: Total Variation distance metric used to define distribution neighborhood
- **Action**: REPLACE
- **Replacement**: 
  - KL-divergence
  - Wasserstein distance
  - Hellinger distance
- **Metrics**: perplexity, repetition frequency, MAUVE

### Adversarial Nature Ablation
- **Ablated Part**: Adversarial nature player in the two-player game
- **Action**: REPLACE
- **Replacement**: 
  - random perturbation
  - fixed distribution shift
  - no adversary
- **Metrics**: perplexity, repetition frequency, MAUVE

</div>