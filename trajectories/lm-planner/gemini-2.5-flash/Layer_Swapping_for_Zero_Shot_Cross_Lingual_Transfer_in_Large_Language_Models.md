<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Layer_Swapping_for_Zero_Shot_Cross_Lingual_Transfer_in_Large_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Layer Swapping for Zero-Shot Cross-Lingual Transfer in Large Language Models" proposes a novel model merging technique where top and bottom transformer layers from a language-expert model are swapped into a task-expert model (fine-tuned on English math data) to improve performance on the task in the target language. The core idea is based on a preliminary analysis suggesting that language-specific parameters are concentrated in the outer layers, while task-specific parameters are in the middle layers.

The paper presents several experiments comparing the layer swapping method to baselines like individual experts, model souping, TIES-merging, and joint SFT (Section 5). It demonstrates that layer swapping generally outperforms these baselines on the MGSM benchmark across four target languages.

Section 4.2 discusses the configuration of the layer swapping method, mentioning empirical testing of the number of layers to swap at the bottom (`b`), the number of layers to swap at the top (`u`), and the transition zone layers (`tb`, `tu`). It states that a "wide range of possible configurations" were effective and that results were "largely equivalent within this range," although some patterns were observed (e.g., lower-resource languages benefiting from more language layers). The paper provides a default configuration (`b=5`, `u=2`, `tb=1`, `tu=1` for a 32-layer model) but does not present a systematic ablation study showing the performance impact of varying these crucial parameters.

Based on this, two important missing ablation studies are:

1.  **Varying the number of swapped layers:** The number of layers swapped from the language expert (`b` and `u`) is the most fundamental parameter of the layer swapping method. While the paper mentions testing ranges, a systematic ablation showing how performance changes as `b` and `u` vary would provide critical evidence for the hypothesis about layer specialization and the robustness of the method to these choices. This is more important than the transition zone as it directly tests the core layer-swapping mechanism.
2.  **Ablating the transition zone:** The paper states that the transition zone did not provide statistically significant empirical benefit in their setting but is still presented as a central component. An explicit ablation comparing performance with and without the transition zone would clarify its contribution (or lack thereof) and whether it's a necessary part of the method or merely a theoretically motivated addition that doesn't impact performance significantly in practice.

These two ablations directly investigate the impact of the key configurable components of the layer swapping methodology, which are currently described qualitatively or with limited empirical comparison in the paper. The primary metric used in the paper for evaluating the merged models is the MGSM score (average and max across languages/pairs), which should be used for these ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablate Swapped Layer Count
- **Ablated Part**: Number of top and bottom transformer layers swapped from the language expert
- **Action**: REPLACE
- **Replacement**: 
  - {'bottom_layers': 0, 'top_layers': 0}
  - {'bottom_layers': 3, 'top_layers': 1}
  - {'bottom_layers': 5, 'top_layers': 2}
  - {'bottom_layers': 8, 'top_layers': 4}
- **Metrics**: MGSM avg, MGSM max

### Ablate Transition Zone
- **Ablated Part**: Transition zone layers between swapped sections
- **Action**: REMOVE
- **Metrics**: MGSM avg, MGSM max

</div>