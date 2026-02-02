<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/TimeSuite__Improving_MLLMs_for_Long_Video_Understanding_via_Grounded_Tuning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One key component introduced in this paper is the explicit temporal grounding supervision via the new “Temporal Grounded Caption” task. While the paper extensively analyzes the impact of TAPE and token shuffling (including replacing token shuffling with pooling or clustering), it does not include an ablation study that isolates the effect of the grounded captioning objective itself. Evaluating the model’s performance when using a regular captioning task (i.e. where the model only generates descriptive captions without precise timestamp predictions) versus the proposed Temporal Grounded Caption would clarify how much the explicit temporal supervision contributes to reducing hallucinations and boosting temporal grounding accuracy. Additionally, although the token shuffling module is compared with other compression strategies, the sensitivity of its key hyperparameter – the merging factor (m) that determines how many adjacent tokens are concatenated – is not explored. Investigating different values of m can provide insights into the optimal trade-off between token compression (and computational efficiency) and retention of fine-grained temporal details. These two proposed ablations address major components central to the method but missing from the current experimental analysis.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Temporal Grounded Caption Task
- **Ablated Part**: The explicit instruction tuning task that forces the model to output both detailed video descriptions and corresponding timestamp predictions (Temporal Grounded Caption)
- **Action**: REPLACE
- **Replacement**: 
  - Regular Captioning Task
  - Simplified Temporal Captioning without timestamp prediction
- **Metrics**: Charades-STA R@1 (IOU=0.5), QVHighlight mAP, Egoschema Accuracy, VideoMME Accuracy, Hallucination Rate (if available)

### Ablation of Token Shuffle Compression Factor
- **Ablated Part**: The hyperparameter (m) in the Token Shuffle module that controls how many adjacent tokens are merged
- **Action**: REPLACE
- **Replacement**: 
  - m=2
  - m=4
  - m=8
- **Metrics**: Charades-STA R@1 (IOU=0.5), QVHighlight mAP, Egoschema Accuracy, VideoMME Accuracy

</div>