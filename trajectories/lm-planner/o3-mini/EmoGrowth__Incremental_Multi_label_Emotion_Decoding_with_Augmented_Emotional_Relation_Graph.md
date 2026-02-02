<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/EmoGrowth__Incremental_Multi_label_Emotion_Decoding_with_Augmented_Emotional_Relation_Graph

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We identified two aspects that were not explicitly ablated in the paper. First, although the paper demonstrates the effectiveness of its augmented Emotional Relation Graph (ERG) module with label disambiguation, it does not isolate the benefit of incorporating historical label correlations across tasks. A missing ablation is to replace the proposed augmented ERG (which integrates previous task information and refines soft labels via graph-based label propagation) with a static ERG computed solely from the current task’s co-occurrence statistics. This study could reveal whether the historical integration truly contributes to mitigating the past-missing partial label problem. Second, the method employs relation‐based knowledge distillation (RKD) by aligning model features with a multi‐dimensional affective space (e.g., capturing both arousal and valence) to alleviate the future-missing partial label problem. However, it is unclear whether the multi-dimensionality is necessary. An ablation that uses only a single dimension (either arousal or valence) as the teacher signal might provide insights into the relative contribution of each affective dimension. Both ablations would be evaluated with the commonly used metrics: mAP, maF1, and miF1.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Static ERG Ablation
- **Ablated Part**: Augmented Emotional Relation Graph (ERG) module that integrates historical ERG and performs label disambiguation
- **Action**: REPLACE
- **Replacement**: 
  - Static ERG computed solely from current task co-occurrence statistics
- **Metrics**: mAP, maF1, miF1

### Single-Dimension Affective KD Ablation
- **Ablated Part**: Relation-based knowledge distillation module that aligns features using a multi-dimensional affective space
- **Action**: REPLACE
- **Replacement**: 
  - Using only Arousal
  - Using only Valence
- **Metrics**: mAP, maF1, miF1

</div>