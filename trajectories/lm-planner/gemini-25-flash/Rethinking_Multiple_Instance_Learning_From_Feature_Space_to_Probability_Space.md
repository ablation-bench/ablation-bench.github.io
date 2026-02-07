<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Rethinking_Multiple_Instance_Learning_From_Feature_Space_to_Probability_Space

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Rethinking Multiple-Instance Learning From Feature Space to Probability Space" proposes PSMIL, a novel approach that tackles feature drift and selection drift in deep MIL by operating in probability space. The core contributions are the Probability-Space Alignment (PSAli) objective and the Probability-Space Attention Pooling (PSAtt).

The paper includes an ablation study in Table 3, which evaluates the contribution of PSAli and PSAtt on challenging simulated datasets (CIFAR-10 and CIFAR-100) where traditional methods (ABMIL+, DEMIL+) with trainable feature extractors degrade. The existing ablations show:
1.  Traditional methods with fixed feature extractors (ABMIL, DEMIL) perform reasonably well on pre-extracted features.
2.  Traditional methods with trainable feature extractors (ABMIL+, DEMIL+) degrade on complex data.
3.  Adding PSAli to trainable traditional methods (ABMIL++, DEMIL++) significantly improves performance and prevents degradation.
4.  Adding PSAtt *in addition to PSAli* (PSMIL variants) further improves performance compared to ABMIL++/DEMIL++.
5.  The impact of the λ parameter for the PSAli objective is explored.

Based on this analysis, two important missing ablation studies are identified:

1.  **Individual contribution of PSAtt:** The existing ablation shows PSAtt's benefit *when combined with PSAli*. It is not clear from Table 3 whether PSAtt *alone* (without PSAli) can prevent degradation or improve performance compared to the baseline trainable models (ABMIL+, DEMIL+). Evaluating a configuration with a trainable feature extractor, no PSAli, but with PSAtt would isolate the effect of the probability-space attention mechanism on its own. This is crucial to understand if PSAtt independently contributes to mitigating selection drift as claimed, or if its effectiveness is contingent on the stabilized features provided by PSAli.

2.  **PSAli Pseudo-labeling Strategy:** The PSAli objective relies on a specific pseudo-labeling strategy derived from multiplying probabilities across augmented views (Proposition 2). While the paper provides a theoretical justification for its optimality, an empirical comparison against alternative, simpler pseudo-labeling strategies would strengthen the claim and demonstrate the practical importance of this specific design choice within PSAli. For example, comparing the proposed multiplicative strategy to simply averaging probabilities across augmented views or using the pseudo-label from the original instance could reveal its empirical advantage. This ablation should be performed on a model that includes the PSAli objective, such as ABMIL++.

These two ablations are ranked by importance. The first one (PSAtt alone) is arguably more critical as it tests the independent contribution of one of the two main proposed mechanisms. The second one (PSAli pseudo-labeling) investigates a specific design detail within one of the mechanisms. Both are important for a complete understanding of PSMIL's performance attribution.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### PSAtt Only (Trainable RL)
- **Ablated Part**: Probability-Space Alignment (PSAli) objective
- **Action**: REMOVE
- **Metrics**: Acc

### PSAli Pseudo-labeling Strategy
- **Ablated Part**: Pseudo-labeling strategy within the Probability-Space Alignment (PSAli) objective
- **Action**: REPLACE
- **Replacement**: 
  - Average probabilities across augmented views
  - Pseudo-label from original instance only
- **Metrics**: Acc

</div>