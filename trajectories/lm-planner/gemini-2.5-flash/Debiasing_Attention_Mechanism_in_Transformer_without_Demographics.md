<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Debiasing_Attention_Mechanism_in_Transformer_without_Demographics

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Debiasing Attention Mechanism in Transformer without Demographics" proposes a novel method to mitigate bias in transformers by modifying the attention mechanism. The method consists of two main components: 1) debiasing attention weights by normalizing and taking the absolute value of queries and keys, and 2) performing local alignment on value vectors selected based on these debiased attention weights using supervised contrastive learning. The paper also highlights a GPU-efficient strategy of applying this method only to the last encoder layer, particularly for pre-trained models.

The paper includes an ablation study in Appendix F, which investigates the importance of three aspects:
1.  Removing the local alignment component (`w/o local alignment`).
2.  Removing the debias attention component (normalization and absolute value) (`w/o debias attention`).
3.  Removing only the absolute value operation from the debias attention component (`w/o absolute value`).

This existing ablation study demonstrates that both the debias attention and local alignment components contribute to the method's fairness performance, with debias attention being particularly crucial.

However, based on the method description and experimental setup, there are two important aspects that are not fully ablated:

1.  **Location of Debiasing:** The paper states that the debiasing method is applied only to the *last encoder layer* (Section 3.1, 3.4, Appendix C). While Section 3.4 discusses this as an efficiency strategy for pre-trained models, the method is also applied this way when training from scratch (Section 4.1, Appendix C). The paper claims bias is spread across all layers. An ablation comparing applying the debiasing method (both attention debiasing and value alignment) to *all* encoder layers versus *only the last* encoder layer (as done in the paper) is missing. This would clarify the impact of this architectural choice on fairness, accuracy, and computational cost when training from scratch, independent of the pre-training efficiency argument. This is a fundamental design choice that warrants investigation.

2.  **Value Selection Strategy for Local Alignment:** The local alignment step selects value vectors corresponding to the *top t* attention weights computed using the *debiased* queries and keys. The paper shows the effect of varying `t` in the fairness-accuracy trade-off plot (Figure 2), but it doesn't formally ablate the *strategy* of selection. Specifically, it would be valuable to understand if selecting value vectors based on the *original* attention weights (before debiasing) would yield different results. This would test the necessity of the attention debiasing step for the effectiveness of the subsequent value alignment step, beyond just removing the entire alignment component as done in the existing ablation.

Ranking these, the location of debiasing seems like a more significant architectural decision and potentially has a larger impact on overall performance and efficiency characteristics when training from scratch. The value selection strategy is also important as it tests the interaction between the two core debiasing steps. Therefore, I will suggest the location ablation as the most important missing one, and the value selection strategy as the second.

The metrics used in the paper's experiments and existing ablations are Accuracy (ACC), Demographic Parity (DP), Equal Opportunity (EOp), Equalized Odds (EOd), Energy Consumption (E(Wh)), and GPU Memory (GPU (MiB)). These should be used for the suggested ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Debiasing Location
- **Ablated Part**: Application scope of the debiasing method (attention debiasing and value alignment) across transformer layers.
- **Action**: REPLACE
- **Replacement**: 
  - Apply to last encoder layer only
  - Apply to all encoder layers
- **Metrics**: ACC, DP, EOp, EOd, E(Wh), GPU (MiB)

### Value Selection Strategy
- **Ablated Part**: Criterion used to select value vectors for local alignment.
- **Action**: REPLACE
- **Replacement**: 
  - Top t based on debiased attention
  - Top t based on original attention
- **Metrics**: ACC, DP, EOp, EOd

</div>