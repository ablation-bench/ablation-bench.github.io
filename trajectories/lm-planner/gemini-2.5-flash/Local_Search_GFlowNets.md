<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Local_Search_GFlowNets

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Local Search GFlowNets" proposes an extension to GFlowNets that incorporates a local search step (Step B) into the standard GFN training loop (Steps A and C). The core idea is to refine initially sampled trajectories (Step A) using a local search mechanism guided by the learned forward and backward policies (P_F and P_B). These refined trajectories, along with the original ones, are added to a training dataset D, which is then used to train the GFN policies (Step C).

The paper includes several ablation studies:
1.  Comparison of deterministic vs. stochastic filtering in the local search (Appendix B.2).
2.  Analysis of the number of local search revision steps (I) and initial samples (M), keeping the total evaluation budget constant (Appendix B.3).
3.  Analysis of the number of destruction/reconstruction steps (K) in the local search (Appendix B.5).
4.  Analysis of the local search acceptance rate (Appendix B.6).
5.  Comparison with different GFN training objectives (TB, DB, SubTB, etc.) (Table 1, Table 2).

While these ablations cover aspects of the local search mechanism itself (Step B) and its integration with different GFN objectives, they do not fully explore how the *output* of the local search (the refined trajectories) is used to train the GFN policies in Step C. Specifically, two key aspects of the training data handling are mentioned:
*   The training dataset D includes *both* accepted and rejected trajectories from the refinement step (Algorithm 1, line 7).
*   The training uses reward-based prioritized replay training (PRT) from dataset D (Section 4.3).

These two design choices are crucial for understanding how the local search results influence the GFN training. Including rejected (potentially lower-reward) trajectories might help maintain diversity or prevent overfitting to high-reward modes, while PRT explicitly biases training towards the higher-reward samples generated or refined by the method. Ablating these aspects would provide valuable insights into the training dynamics and the contribution of these specific choices to the reported performance gains.

Therefore, I propose two missing ablation studies:
1.  **Training Data Composition:** Investigate the effect of *not* including the rejected trajectories in the training dataset D. This tests whether training on lower-reward, but explored, trajectories is beneficial or detrimental.
2.  **Training Data Sampling:** Investigate the effect of using uniform sampling from the dataset D instead of the reward-based prioritized replay training (PRT). This tests whether explicitly prioritizing high-reward samples during batch selection is necessary for the method's success.

These ablations are important because they directly address how the novel local search component interacts with the standard GFN training process, which is a core part of the LS-GFN method. The metrics used in the paper (Accuracy, Number of Modes, Top 100 Reward, Top 100 Diversity, Uniq. Fraction) are appropriate for evaluating the impact of these changes.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Training Data Composition
- **Ablated Part**: Inclusion of trajectories rejected by the filtering step in the training dataset D.
- **Action**: REMOVE
- **Metrics**: Accuracy, Number of Modes, Top 100 Reward, Top 100 Diversity, Uniq. Fraction

### Training Data Sampling
- **Ablated Part**: Reward-based prioritized sampling strategy for training batches from dataset D.
- **Action**: REPLACE
- **Replacement**: 
  - Uniform sampling from D
- **Metrics**: Accuracy, Number of Modes, Top 100 Reward, Top 100 Diversity, Uniq. Fraction

</div>