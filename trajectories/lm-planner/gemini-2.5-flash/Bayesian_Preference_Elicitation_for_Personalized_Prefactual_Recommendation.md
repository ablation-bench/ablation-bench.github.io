<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Bayesian_Preference_Elicitation_for_Personalized_Prefactual_Recommendation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a Bayesian preference elicitation (BPE) framework for personalized prefactual recommendation. The core idea is to learn an individual's cost function, modeled as a Mahalanobis distance with an unknown matrix A0, through sequential pairwise comparisons. The framework uses a Wishart prior for the cost matrix Ã, selects questions by maximizing the asymptotic mutual information between the response and Ã, and updates the posterior distribution via KL divergence minimization. Finally, it generates graph-based sequential recourse by minimizing the expected cost under the posterior distribution.

The paper includes several experiments:
1.  Comparison with graph-based (FACE) and non-graph-based (Wachter, DiCE) recourse methods, evaluating cost (Mahalanobis and L1) and validity (Tables 1, 2, 5, 6).
2.  Analysis of the effect of the number of questions (T) on the mean rank of recommended recourses, showing convergence towards the true cost function (Figure 2).
3.  Demonstration of the posterior update loss convergence (Figure 3).
4.  Visualization of the posterior distribution of Mahalanobis distances for different noise levels (κ) (Figures 4-7).

While these experiments demonstrate the overall effectiveness and some properties of the method, several key components and design choices are not ablated:

1.  **Question Selection Strategy:** The paper highlights the mutual-information-maximization question-answering scheme as a contribution and provides an analytical expression for asymptotic mutual information. However, it does not compare this specific question selection strategy (maximizing asymptotic MI) against alternative, simpler strategies. For instance, a baseline could be random selection of question pairs, or selecting pairs that are expected to maximally reduce the variance of the estimated cost matrix parameters. Ablating this component would demonstrate the value added by the sophisticated MI-based selection.
2.  **Bayesian Framework vs. Point Estimation:** The method's novelty lies in its Bayesian approach, modeling the cost matrix as a distribution and updating beliefs. An alternative, simpler approach would be to treat the cost matrix A0 as a deterministic unknown and learn a point estimate directly from pairwise comparisons using optimization (e.g., maximum likelihood estimation based on the BTL model). An ablation comparing the full Bayesian framework (learning a distribution) to such a non-Bayesian point estimation approach would highlight the benefits of modeling uncertainty, especially with limited data (few questions T).

Based on their importance to the core claims and novelty of the paper, these two ablations are significant missing pieces. The question selection strategy is a specific mechanism proposed for efficient elicitation within the framework, while the Bayesian vs. point estimation comparison evaluates the fundamental modeling choice.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Question Selection Strategy
- **Ablated Part**: Strategy for selecting pairwise comparison questions (mutual information maximization)
- **Action**: REPLACE
- **Replacement**: 
  - Random selection
- **Metrics**: Cost (Mahalanobis), Cost (L1), Validity, Mean Rank

### Ablation: Bayesian vs. Point Estimation
- **Ablated Part**: Bayesian framework for learning the cost matrix distribution
- **Action**: REPLACE
- **Replacement**: 
  - Point estimation of cost matrix from pairwise comparisons
- **Metrics**: Cost (Mahalanobis), Cost (L1), Validity, Mean Rank

</div>