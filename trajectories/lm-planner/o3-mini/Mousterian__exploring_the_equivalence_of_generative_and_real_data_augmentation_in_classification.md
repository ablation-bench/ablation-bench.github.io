<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Mousterian__exploring_the_equivalence_of_generative_and_real_data_augmentation_in_classification

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One key component of the work is the use of a CLIP-Filter strategy that removes the bottom 20% of generated synthetic images to ensure high quality. However, the paper does not explore how sensitive the classification performance is to this specific filtering threshold. Varying this threshold might affect both the quality–diversity trade-off of the synthetic data and thus the overall effectiveness of generative data augmentation. This missing ablation is important because it directly impacts the design decision regarding synthetic data pre‐processing and can help identify an optimal rejection threshold.

Another fundamental design choice in the paper is the mixed training strategy, where real and synthetic images are jointly used during training. While the experiments cover varying mixing ratios, the study does not investigate alternative training protocols such as sequential training (i.e., pre-training a model on synthetic data and then fine-tuning on real data). Assessing the performance differences between joint and sequential training could offer additional insights into the most effective way to leverage synthetic data augmentation especially in low-data regimes.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: CLIP Filter Threshold Sensitivity
- **Ablated Part**: Synthetic data quality control via the CLIP-Filter, which currently excludes the bottom 20% of images
- **Action**: REPLACE
- **Replacement**: 
  - exclude bottom 10%
  - exclude bottom 20%
  - exclude bottom 30%
- **Metrics**: Top-1 Accuracy, FID, Inception Score

### Ablation: Joint vs Sequential Training Strategy
- **Ablated Part**: The mixed training paradigm for integrating real and synthetic data
- **Action**: REPLACE
- **Replacement**: 
  - joint training (mixed real-synthetic)
  - sequential training: pre-train on synthetic then fine-tune on real
- **Metrics**: Top-1 Accuracy, Improvement Ratio (IR)

</div>