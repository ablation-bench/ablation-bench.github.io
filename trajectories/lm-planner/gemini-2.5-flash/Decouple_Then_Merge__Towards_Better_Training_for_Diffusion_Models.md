<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Decouple_Then_Merge__Towards_Better_Training_for_Diffusion_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Decouple-Then-Merge: Towards Better Training for Diffusion Models" proposes a novel framework (DeMe) to mitigate gradient conflicts during diffusion model training. The core idea is to first decouple the training by finetuning separate models on different timestep ranges, incorporating specific techniques (Consistency Loss, Probabilistic Sampling, Channel-wise Projection), and then merging these finetuned models into a single model.

The paper includes an ablation study in Table 3, which evaluates the contribution of the three proposed training techniques (Probabilistic Sampling, Consistency Loss, Channel-wise Projection) on CIFAR10 when using N=8 timestep ranges. It shows that dividing into ranges (N=8 vs N=1) is crucial, and each technique provides additional improvement. Appendix F includes sensitive studies on the number of ranges N and the probability p for probabilistic sampling, showing how FID changes with these parameters.

While these ablations are informative, there are a couple of key aspects of the DeMe framework that could benefit from further investigation through ablation studies:

1.  **Model Merging Strategy:** The paper's second core step is merging the finetuned models. It uses a task vector approach (Equation 8) where the merged model is the pretrained model plus a weighted sum of task vectors (difference between finetuned and pretrained parameters). The weights `w_i` are determined via grid search. The paper shows the performance *after* merging is generally better than *before* merging (ensemble), but it doesn't ablate *how* the merging is done. Specifically, the impact of the weighting strategy `w_i` is not explored. A simple baseline for merging task vectors is uniform averaging (w_i = 1/N). Ablating the grid search optimization of `w_i` against a uniform weighting scheme would clarify if the performance gain comes from the specific optimized weights or simply from combining the task vectors through averaging. This is a crucial part of the "Merge" step.

2.  **Impact of Number of Ranges (N) on Final Merged Model:** The sensitive study in Appendix F (Figure 9) shows the FID for different N values. However, it's not explicitly stated if these results are for the final *merged* model using all techniques. Table 3 only compares N=1 (baseline) and N=8 with different technique combinations, but doesn't show the final merged performance for N=8 or other N values like N=2 or N=4 in a clear comparative table. A dedicated ablation study presenting the final performance (after merging with the full DeMe pipeline) for different values of N (e.g., N=2, 4, 8) alongside the baseline (N=1, no DeMe) would provide a clearer understanding of the trade-off between the number of decoupled tasks and the final model quality. This would complement the sensitive study and the partial ablation in Table 3.

Based on this analysis, the two most important missing ablations are related to the merging strategy and a clearer evaluation of the impact of N on the final merged model performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Merging Weights
- **Ablated Part**: The method for determining the merging weights (w_i) for task vectors.
- **Action**: REPLACE
- **Replacement**: 
  - Uniform weights (w_i = 1/N)
  - Grid search optimized weights (as in paper)
- **Metrics**: FID, CLIP Score

### Ablation on Number of Timestep Ranges (N)
- **Ablated Part**: The number of non-overlapping timestep ranges (N) used for decoupling.
- **Action**: REPLACE
- **Replacement**: 
  - 2
  - 4
  - 8
- **Metrics**: FID, CLIP Score

</div>