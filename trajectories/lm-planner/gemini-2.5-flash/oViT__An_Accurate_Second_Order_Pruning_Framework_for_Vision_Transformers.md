<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/oViT__An_Accurate_Second_Order_Pruning_Framework_for_Vision_Transformers

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "oViT: An Accurate Second-Order Pruning Framework for Vision Transformers" introduces a novel second-order pruning method tailored for Vision Transformers (ViTs). The core contributions include the oViT pruning algorithm itself, which leverages second-order information and handles weight correlations efficiently, and a post-pruning recovery framework involving specific learning rate schedules and augmentation recipes. The paper also proposes an efficient pipeline to obtain models at multiple sparsity targets in a single gradual pruning run.

The paper includes several ablation studies:
1.  **Comparison of Pruning Methods:** Extensive comparisons are made between oViT and other methods (Magnitude, GrW, WoodFisher, M-FAC, SViTE, AC/DC) in one-shot, one-shot + fine-tuning, and gradual pruning settings across various ViT and CNN models (Figure 3, Table 1, Table 2, Appendix C, D, J, K, M). This validates the effectiveness of the oViT pruner.
2.  **Post-Pruning Recovery Components:** Ablations investigate the impact of different learning rate schedules (cyclic linear vs. cosine annealing) and augmentation recipes (light1 vs. deit) on accuracy recovery during fine-tuning (Figure 4, Appendix B). This highlights the importance of the recovery strategy.
3.  **Hyperparameter Tuning:** The paper explores the effect of hyperparameters like the number of gradients, dampening constant (λ), and block size on oViT and WoodFisher performance in the one-shot setting (Appendix G). It also studies the effect of multiple recomputations.

Based on the analysis, two important missing ablation studies are identified:

1.  **Block Size in Gradual Pruning:** While Appendix G ablates the block size for one-shot pruning, the main results and the strength of oViT are demonstrated in the gradual pruning setting (Table 2). The block size is a critical parameter influencing how local (within-block) and global correlations are handled in the second-order calculation and subsequent weight updates/selection. An ablation studying the impact of different block sizes specifically within the gradual pruning framework would provide deeper insight into how this parameter affects the iterative pruning and fine-tuning process and the final accuracy-sparsity trade-off. This is crucial because the iterative nature of gradual pruning might interact differently with block size choices compared to one-shot pruning.
2.  **Efficiency and Accuracy of the Sparsity Sweep Pipeline:** The paper presents the "Efficient Pipeline for Sparsity Sweeps" as a practical advantage, allowing multiple sparsity checkpoints in a single run. However, it doesn't explicitly compare the performance (both accuracy and total computational cost/epochs) of this single-run sweep approach against the traditional method of running separate gradual pruning procedures for each target sparsity level. An ablation comparing these two strategies would quantitatively validate the efficiency claim and determine if there is any accuracy degradation associated with obtaining multiple checkpoints from a single sweep run compared to optimizing each target independently.

These two ablations are ranked by importance, with the block size ablation in the gradual setting being slightly more critical as it directly probes a core algorithmic detail within the paper's primary experimental setup (gradual pruning).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Gradual Pruning Block Size Ablation
- **Ablated Part**: Block size used in the oViT second-order pruning algorithm during gradual pruning.
- **Action**: REPLACE
- **Replacement**: 
  - 16
  - 64
  - 256
- **Metrics**: Top1-Accuracy, FLOP Reduction

### Sparsity Sweep Pipeline Ablation
- **Ablated Part**: The efficient pipeline for obtaining multiple sparsity targets in a single gradual pruning run.
- **Action**: REPLACE
- **Replacement**: 
  - Independent gradual pruning runs for each target sparsity (e.g., 75%, 90%)
- **Metrics**: Top1-Accuracy, Total Training Epochs

</div>