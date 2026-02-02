<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/L2B__Learning_to_Bootstrap_for_Combating_Label_Noise

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "L2B: Learning to Bootstrap for Combating Label Noise" proposes a novel method that jointly reweights the loss from real noisy labels and pseudo-labels using a meta-learning approach guided by a small clean validation set. The core idea is to learn per-sample weights (α and β) for these two loss terms.

The paper includes several ablation studies in Section 4.3:
1.  **Importance of α and β:** This study investigates the contribution of the real label loss (setting α=0), the pseudo-label loss (setting β=0, which is equivalent to the L2RW baseline), and the constraint α+β=1 (like original bootstrapping). This effectively ablates the joint reweighting mechanism and the relaxation of the α+β=1 constraint.
2.  **Parameter Normalization:** This study compares different normalization functions (Eq. 9, Sigmoid, Softmax) for the learned weights α and β, showing their impact on stability and performance across datasets.
3.  **Comparison with MLC:** This compares L2B against another meta-learning-based method for label correction.

While these ablations cover key aspects of the loss formulation and weight learning, there are other important components and dependencies that could benefit from further investigation through ablation.

Based on the paper's description and common practices in noisy label learning and meta-learning, two important missing ablations are:

1.  **Impact of the Clean Validation Set Size:** The meta-learning framework relies on a small clean validation set (Dval) to guide the learning of the weights α and β. The paper uses specific sizes (1000 for CIFAR, 640 for ISIC) and mentions the need for this set as a potential limitation for future work. An ablation studying the performance sensitivity to the size of this clean set is crucial. It would inform practitioners about the minimum required size for effective training and quantify the trade-off between validation set size and performance. This directly addresses a practical concern and a dependency of the core meta-learning mechanism.
2.  **Impact of the Warm-up Period:** The paper mentions using a warm-up period (10 epochs for CIFAR, 1 epoch for ISIC) before the main training. Warm-up is a common technique in noisy label learning to allow the model to learn initial robust features before applying noise-handling mechanisms. Ablating the duration of this warm-up period (including removing it entirely) would demonstrate its necessity and optimal length for the L2B method. This helps understand the training dynamics and whether L2B is robust even without an explicit warm-up phase.

These two ablations are important because they investigate critical practical aspects (data requirements) and training procedures (warm-up) that are essential for successfully applying and understanding the L2B method. They are not covered by the existing ablations which focus more on the loss formulation and weight normalization.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Clean Validation Set Size
- **Ablated Part**: Size of the clean validation set (Dval) used for meta-learning
- **Action**: REPLACE
- **Replacement**: 
  - Smaller size (e.g., 100, 200, 500 for CIFAR)
  - Larger size (e.g., 2000 for CIFAR)
- **Metrics**: Test Accuracy (%)

### Ablation: Warm-up Period
- **Ablated Part**: Duration of the warm-up phase before applying L2B's meta-learning updates
- **Action**: REPLACE
- **Replacement**: 
  - 0 epochs (no warm-up)
  - 5 epochs
  - 20 epochs
- **Metrics**: Test Accuracy (%)

</div>