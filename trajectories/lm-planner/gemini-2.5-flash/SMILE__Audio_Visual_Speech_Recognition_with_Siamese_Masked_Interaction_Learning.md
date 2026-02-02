<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/SMILE__Audio_Visual_Speech_Recognition_with_Siamese_Masked_Interaction_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user requested up to two missing ablation studies for the paper "SMILE: Audio-Visual Speech Recognition with Siamese Masked Interaction Learning". I need to identify key components of the SMILE framework and determine which ones have not been adequately ablated in the paper's experimental section.

The core components of SMILE are:
1.  Siamese Masked Interaction Learning (combining Siamese architecture, masking, and MRM loss).
2.  Adaptive Dynamic Multimodal Fusion.
3.  Temporal-wise feature concatenation.
4.  Audio-Visual Adapter.
5.  Combined loss function (MRM + CE).

The paper includes several ablation studies:
*   Table 3 ablates the overall effectiveness of Adaptive Multimodal Fusion and Siamese Masked Interaction Learning (comparing full SMILE to Masked Feature Augmentation, and Masked Feature Augmentation to Adaptive Fusion + Baseline, and Adaptive Fusion + Baseline to Baseline). This effectively shows the contribution of the main functional modules.
*   Table 4a ablates different Siamese training strategies (stop gradient, EMA, etc.).
*   Table 4b ablates masking rates and lengths.
*   Table 5a, 5b, 5c, 5d provide further ablations on masking types, masking strategies (reconstruction target), prediction heads for the loss, and loss weights (alpha, beta).

Based on this review, the functional components and their training strategies/hyperparameters seem reasonably well-ablated. However, two structural design choices are present in the baseline and the final model but are not ablated against alternatives or removal:

1.  **Temporal-wise Feature Concatenation:** The paper explicitly states they use temporal concatenation (2T x B x C) and initialize from a model (Shi et al., 2022a) that uses channel-wise concatenation (T x B x 2C). This is a fundamental difference in how modalities are combined early on. An ablation comparing the performance of SMILE with temporal concatenation versus channel-wise concatenation would be crucial to justify this architectural choice.
2.  **Audio-Visual Adapter:** This module is introduced specifically because of the temporal concatenation and the initialization from a channel-concatenation model. The baseline itself includes this adapter. An ablation study removing this adapter from the temporal-concatenation setup (either the baseline or the full SMILE model) would show its necessity and impact, independent of the concatenation strategy comparison.

Both of these ablations are important for understanding the model's architecture. The choice of concatenation strategy is arguably more fundamental as it dictates the input shape to the encoder, while the adapter is a module added on top. Therefore, I will prioritize the concatenation strategy ablation as the first suggestion and the adapter removal as the second.

The metrics used throughout the paper, including the existing ablation studies, are Word Error Rate (WER) on the LRS2 and LRS3 datasets, particularly in the low-resource settings. I will use these metrics.

For the concatenation ablation, the action is REPLACE, with the replacement being "Channel-wise concatenation". For the adapter ablation, the action is REMOVE.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Channel Concatenation
- **Ablated Part**: Method of combining audio and visual features before the encoder (temporal-wise concatenation)
- **Action**: REPLACE
- **Replacement**: 
  - Channel-wise concatenation (T x B x 2C)
- **Metrics**: WER

### Ablation: Remove Audio-Visual Adapter
- **Ablated Part**: Audio-Visual Adapter module placed before the encoder layers
- **Action**: REMOVE
- **Metrics**: WER

</div>