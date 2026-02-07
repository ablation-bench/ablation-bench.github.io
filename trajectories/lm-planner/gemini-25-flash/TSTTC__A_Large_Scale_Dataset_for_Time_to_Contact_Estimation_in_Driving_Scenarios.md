<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/TSTTC__A_Large_Scale_Dataset_for_Time_to_Contact_Estimation_in_Driving_Scenarios

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "TSTTC: A Large-Scale Dataset for Time-to-Contact Estimation in Driving Scenarios" introduces a new dataset for monocular TTC estimation and provides two baseline methods, Pixel MSE and Deep Scale. The dataset is notable for its scale, focus on driving scenarios (urban and highway), and the inclusion of NeRF-generated data to augment rare cases, particularly those with small TTC values. The baseline methods estimate TTC by classifying the scale ratio between objects in consecutive frames, leveraging either pixel-level similarity (Pixel MSE) or deep features (Deep Scale).

The paper includes several ablation studies for the baseline methods, investigating the influence of hyperparameters like the number of scale bins, the center shift operation, the target size for grid sampling, the kernel size, and the frame gap between reference and target frames. It also ablates the *amount* of NeRF data added to the training set.

Based on the paper's contributions and existing ablations, two important missing ablation studies are identified:

1.  **Direct evaluation of NeRF augmentation:** While the paper ablates the *amount* of NeRF data, it doesn't directly compare training *with* NeRF data versus training *only* on the real data subset. This ablation is crucial to quantify the actual benefit of the NeRF augmentation strategy, especially for the crucial small TTC cases it was designed to address.
2.  **Utilization of the full sequence:** The dataset provides 6-frame sequences. The baseline methods, as implied by the frame gap ablation, primarily use a single reference frame relative to the target frame (e.g., frame 0 vs frame 5). An ablation studying whether leveraging information from *multiple* reference frames within the sequence (e.g., combining predictions from all pairs like 0->5, 1->5, ..., 4->5) improves performance would be valuable. This explores how effectively the temporal information provided by the dataset sequence can be utilized beyond a single frame pair.

These two ablations are important because they directly assess the impact of key aspects of the dataset (NeRF augmentation) and the potential for leveraging the dataset's structure (sequence length) in the baseline methods. The metrics used for evaluation should align with those reported in the paper, namely MiD and RTE, broken down by the defined TTC intervals (crucial, small, large, negative).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Impact of NeRF Augmentation
- **Ablated Part**: Inclusion of NeRF-generated data in the training set
- **Action**: REMOVE
- **Metrics**: MiD, MiDc, MiDs, MiDl, MiDn, RTE, RTEc, RTEs, RTEl, RTEn

### Multi-Frame TTC Prediction
- **Ablated Part**: Strategy for utilizing multiple reference frames in the sequence
- **Action**: ADD
- **Replacement**: 
  - Average predictions from multiple reference-target pairs (0->5, 1->5, 2->5, 3->5, 4->5)
- **Metrics**: MiD, MiDc, MiDs, MiDl, MiDn, RTE, RTEc, RTEs, RTEl, RTEn

</div>