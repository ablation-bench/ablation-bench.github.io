<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Decoding_Game__On_Minimax_Optimality_of_Heuristic_Text_Generation_Strategies

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper’s main contributions derive optimal decoding strategies by framing text generation as a Decoding Game between a strategist and an adversarial Nature. The theoretical derivations assume that Nature’s deviation is characterized using the total variation (TV) metric and that the optimal strategy can be obtained via a locally optimal one‐step game. However, two major components have not been interrogated via ablation studies. First, the choice of TV distance to define the adversary’s neighborhood is critical in the theoretical derivation. In practice, one may question the sensitivity of the resulting optimal sampling strategy (and its empirical performance) to the choice of divergence measure. Therefore, an ablation study that replaces TV with alternative measures (such as KL divergence or Wasserstein distance) would illuminate whether the derived truncation-normalization behavior is robust under other distance metrics. Second, the derivations and experimental implementation rely on a “no foresight” assumption where the decoding game is solved locally one-step at a time. While the authors justify this due to computational intractability, it remains unclear whether a multi‐step (lookahead) variant might further improve generation quality. Thus, an ablation study that integrates limited lookahead (e.g. 2‐ or 3‐step planning) into the decoding strategy and compares it with the current one‐step method would help determine the value of additional future context in the adversarial formulation.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Alternative Distance Metric Ablation
- **Ablated Part**: Definition of the adversarial neighborhood using TV distance in the Decoding Game framework
- **Action**: REPLACE
- **Replacement**: 
  - KL divergence
  - Wasserstein distance
- **Metrics**: Perplexity, Repetition, MAUVE

### Multi-step Lookahead Ablation
- **Ablated Part**: The locally optimal one-step decoding strategy (no-foresight assumption) in Game sampling
- **Action**: ADD
- **Replacement**: 
  - 2-step lookahead
  - 3-step lookahead
- **Metrics**: Perplexity, Repetition, MAUVE

</div>