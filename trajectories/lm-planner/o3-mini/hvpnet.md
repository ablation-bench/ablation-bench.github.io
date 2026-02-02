<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/hvpnet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Below are four ablation experiments targeting the most influential components of HVPNeT. The first study removes the dynamic gated aggregation module to assess the impact of its learned, image‐dependent weighting. This tests if a simple uniform averaging of the multi-scale visual features can provide competitive performance. The second experiment replaces the hierarchical multi-scale visual feature combination with a single-scale (i.e., final block) visual feature, which allows us to determine how critical the pyramid structure is for robust entity and relation extraction. The third ablation completely removes the visual prefix injection mechanism, which is responsible for integrating visual clues at every Transformer layer; this experiment evaluates the overall contribution of visual guidance to the textual representation. Finally, the fourth study replaces the dynamic gate with a static (uniform) weighting mechanism to compare against the adaptive decision‐making of the learned gate. All experiments will be assessed via the standard evaluation measures for multimodal NER and MRE (e.g., F1 scores for both tasks).
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Dynamic Gate Removal
- **Ablated Part**: The dynamic gated aggregation module that assigns image-dependent weights to hierarchical visual features
- **Action**: REMOVE
- **Metrics**: F1_NER, F1_RE

### Single-scale Visual Feature
- **Ablated Part**: The hierarchical multi-scaled visual feature aggregation, replaced with only the final block visual feature
- **Action**: REPLACE
- **Replacement**: 
  - final block only
- **Metrics**: F1_NER, F1_RE

### Visual Prefix Removal
- **Ablated Part**: The visual prefix-guided fusion mechanism that integrates visual features into each Transformer layer
- **Action**: REMOVE
- **Metrics**: F1_NER, F1_RE

### Static Gate Replacement
- **Ablated Part**: The dynamic gating mechanism in visual aggregation, replaced with a fixed uniform weighting strategy
- **Action**: REPLACE
- **Replacement**: 
  - uniform weighting
  - static weighting
- **Metrics**: F1_NER, F1_RE

</div>