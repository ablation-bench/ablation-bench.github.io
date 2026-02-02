<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Weakly_supervised_3D_Referring_Expression_Segmentation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper contains extensive ablations on the individual expert components (full‐context, attribute, category) and on the aggregation strategy (MEA vs. average vs. max) as well as on several design choices such as the use of Long‑CLIP and attribute phrase extraction. However, two important questions remain unexamined:
1. The full‐context expert extracts visual context by selecting top‑K frames based on a computed visibility measure. Although the paper ablates the number of selected frames (varying K), it does not compare the effectiveness of this visibility‑based selection against alternative frame selection methods. A missing ablation would replace the visibility‑based frame selection with simpler strategies (e.g., random top‑K selection or using all available frames) to determine how critical the visibility criterion is for capturing effective visual context.
2. After the MEA module computes the consolidated probability distribution over the 3D proposals, the paper adopts a greedy (top‑1 or top‑n) sampling procedure to pick the target instance. However, there is no exploration of how alternative sampling strategies might affect performance. An ablation study can compare the default greedy selection to other selection strategies such as probabilistic (stochastic) sampling or different top‑n voting schemes. Such an analysis will shed light on the sensitivity of the final segmentation performance to the target selection process.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Frame Selection Strategy
- **Ablated Part**: Full-Context Expert's frame selection mechanism that uses visibility scores to select Top-K frames from the video
- **Action**: REPLACE
- **Replacement**: 
  - Random Top-K Frame Selection
  - Using All Frames
- **Metrics**: mIoU, R@1, IoU@0.5, R@3, IoU@0.5

### Ablation: Sampling Strategy in Target Selection
- **Ablated Part**: The strategy for selecting the target instance from the consolidated probability distribution in the MEA module
- **Action**: REPLACE
- **Replacement**: 
  - Greedy Sampling
  - Stochastic (probabilistic) Sampling
  - Top-3 Voting
- **Metrics**: mIoU, R@1, IoU@0.5, R@3, IoU@0.5

</div>