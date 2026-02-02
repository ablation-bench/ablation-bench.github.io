<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/STARS__Self_supervised_Tuning_for_3D_Action_Recognition_in_Skeleton_Sequences

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We identified two potential missing ablation studies that could provide further insight into the contributions of STARS. First, although STARS relies on an MAE-like (MAMP) pretraining stage with a motion‐aware masking strategy, the paper does not study the impact of this specific masking design. An ablation comparing the proposed motion‐aware masking with a uniform random masking approach would clarify whether the computed motion intensities and the subsequent probabilistic mask selection are essential for producing improved representations after contrastive tuning.
Second, in the contrastive tuning stage, STARS partially fine‐tunes the encoder using a layer‐wise learning rate decay to update only the higher layers. While the paper presents an analysis of the decay factor, it does not compare this partial-tuning strategy with alternative tuning schemes. An ablation study investigating full encoder tuning (updating all layers) versus the current partial tuning (and even freezing the encoder) would reveal the sensitivity and contribution of fine-tuning strategy to the final performance. Both ablations, evaluated on metrics such as KNN, linear evaluation and few-shot accuracies, will help assess the core design choices in STARS.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Masking Strategy Comparison
- **Ablated Part**: The masking strategy in the MAMP pretraining stage, specifically the use of motion-aware masking based on motion intensity.
- **Action**: REPLACE
- **Replacement**: 
  - Motion-Aware Masking (as in STARS)
  - Uniform Random Masking
- **Metrics**: NTU-60 XSub Accuracy, NTU-60 XView Accuracy, Few-shot Accuracy (1-/5-shot)

### Ablation: Encoder Fine-Tuning Strategy
- **Ablated Part**: The encoder weight updating method during the contrastive tuning stage.
- **Action**: REPLACE
- **Replacement**: 
  - Full Encoder Tuning
  - Partial Tuning (STARS)
  - Frozen Encoder
- **Metrics**: KNN Accuracy, Linear Evaluation Accuracy, Few-shot Accuracy

</div>