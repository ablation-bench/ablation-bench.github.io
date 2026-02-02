<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Rethinking_Multiple_Instance_Learning_From_Feature_Space_to_Probability_Space

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We identified two critical aspects of PSMIL that were not explicitly ablated in the paper. First, although the paper introduces a probability-space alignment objective that leverages an augmented set A(x) to generate optimal pseudo-labels, it does not examine how different augmentation strategies might influence the alignment’s effectiveness and hence the overall instance representation quality. Varying the augmentation approach (e.g., no augmentation, standard augmentations like random flips and crops, or more aggressive augmentations such as color jitter and rotations) can significantly affect the model’s ability to overcome feature drift. Second, the probability-space attention pooling mechanism relies on a momentum-based update for the class prototype matrix Q with a fixed momentum parameter (γ = 0.001). The choice of momentum is crucial because it controls how quickly the class prototypes adapt to newly extracted features versus maintaining historical stability. A sensitivity analysis by testing alternative momentum values (e.g., 0.0001, 0.01, or 0.1) will shed light on its impact on both bag-level and instance-level performance. These ablations would provide valuable insights into the robustness and tuning of the proposed method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Data Augmentation Influence on Probability-Space Alignment
- **Ablated Part**: The augmented instance set (A(x)) used for generating pseudo-labels in the probability-space alignment objective
- **Action**: REPLACE
- **Replacement**: 
  - No Augmentation
  - Standard Augmentation (flip, crop)
  - Heavy Augmentation (flip, crop, color jitter, rotation)
- **Metrics**: instance-level accuracy, bag-level accuracy

### Momentum Parameter Sensitivity in Class Prototype Update
- **Ablated Part**: The momentum parameter (γ) in the update of the class prototype matrix Q within probability-space attention pooling
- **Action**: REPLACE
- **Replacement**: 
  - 0.0001
  - 0.001
  - 0.01
  - 0.1
- **Metrics**: bag-level accuracy, instance-level accuracy

</div>