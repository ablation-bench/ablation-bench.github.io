<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Active_Fine_Tuning_of_Generalist_Policies

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Active Fine-Tuning of Generalist Policies" proposes AMF, an algorithm for active multi-task fine-tuning that selects demonstrations to maximize information gain about the expert policy. The method relies on a principled information-theoretic criterion (maximizing expected reduction in policy uncertainty given a new demonstration) and introduces practical approximations for neural network policies (AMF-NN), including kernel approximation via loss-gradient embeddings, batch selection, and parameter isolation for forgetting mitigation.

The paper includes several valuable ablation studies and comparisons:
1.  Comparison against uniform task sampling (main baseline).
2.  Evaluation of different forgetting mitigation strategies (parameter isolation vs regularization methods).
3.  Ablation of the batch size used for collecting demonstrations.
4.  Comparison of different uncertainty estimation techniques (loss-gradient embeddings, last-layer embeddings, Dropout) used within the AMF-NN framework.
5.  Comparison against a "rebalancing" baseline (which has privileged access to pre-training task counts).

While these experiments shed light on several practical aspects of AMF-NN, two important areas for ablation studies appear to be missing or not explicitly tested as ablations of core components:

1.  **Ablation of the Information Gain Criterion:** The core of AMF is its task selection criterion based on maximizing expected information gain. The paper compares AMF to uniform sampling, but not directly to other common active learning strategies applied to this multi-task fine-tuning setting. Specifically, comparing the proposed information gain criterion against a simpler uncertainty sampling strategy (e.g., selecting tasks where the current policy is most uncertain, as briefly mentioned in Section 5.4 as a baseline for uncertainty estimation methods) would demonstrate the specific benefit of the AMF criterion's formulation which considers the *reduction* in uncertainty and averages over the target task distribution and states. This would isolate the value of the information gain principle itself over simpler uncertainty-based selection.

2.  **Ablation of the Importance Sampling Approximation:** The practical implementation of AMF-NN relies on importance sampling to estimate expectations over trajectories for tasks that haven't been demonstrated yet (Section 4.2, Equation 3). This approximation is necessary for scalability but can introduce variance or inaccuracies, especially with limited data. An ablation study investigating the impact of this specific approximation, perhaps by comparing the full importance sampling approach to a simpler empirical average over observed trajectories (effectively removing the importance weights), would clarify its contribution and necessity for the method's performance.

Based on their fundamental nature to the AMF algorithm, the ablation of the information gain criterion is arguably the most important missing study, followed by the ablation of the importance sampling approximation which is crucial for the practical scalability of the method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Information Gain Criterion
- **Ablated Part**: Task selection criterion (replacing information gain maximization)
- **Action**: REPLACE
- **Replacement**: 
  - Maximize prior policy entropy (Uncertainty Sampling)
- **Metrics**: Multi-task success rate, Area under success rate curve

### Ablation of Importance Sampling
- **Ablated Part**: Importance sampling weights in the practical objective for occupancy estimation
- **Action**: REMOVE
- **Metrics**: Multi-task success rate, Area under success rate curve

</div>