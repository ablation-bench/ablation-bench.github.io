<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Neuron_Activation_Coverage__Rethinking_Out_of_distribution_Detection_and_Generalization

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Neuron Activation Coverage: Rethinking Out-of-distribution Detection and Generalization" introduces Neuron Activation Coverage (NAC) as a measure of neuron behavior under in-distribution (InD) data, derived from the probability density function (PDF) of a formulated neuron activation state ($\hat{z}$). This NAC is then applied to OOD detection (NAC-UE) and OOD generalization evaluation (NAC-ME).

The paper includes several ablation studies:
1.  **Ablation on the neuron activation state formulation ($\hat{z}$):** Compares the proposed $\hat{z} = \sigma(\mathbf{z} \odot \frac{\partial D\_{\text{KL}}}{\partial \mathbf{z}})$ with using raw neuron output ($\mathbf{z}$) or KL gradients ($\frac{\partial D\_{\text{KL}}}{\partial \mathbf{z}}$) alone (Figure 5, Appendix G.2, Table 16). This is a crucial ablation.
2.  **Ablation on layer choices:** Evaluates NAC-UE performance when using neurons from different layers or combinations of layers (Table 4). This is also important as NAC is layer-dependent.
3.  **Parameter analysis:** Investigates the sensitivity of NAC-UE to hyperparameters like sigmoid steepness ($\alpha$), lower bound ($r$ or $O^*$), and number of bins ($M$) for PDF approximation (Tables 5-7, Appendix D.4). This is a necessary analysis of the method's parameters.
4.  **Efficiency analysis:** Studies the impact of the number of training samples used to build the NAC function (Figure 7, Appendix G.1).
5.  **Weighted layer combination:** Explores weighting the contribution of different layers for NAC-UE instead of simple averaging (Table 17, Appendix G.4).
6.  **NAC entropy for training:** Investigates using NAC entropy as a regularization term during training for OOD generalization (Table 18, Appendix G.5).

While the paper thoroughly ablates the formulation of the neuron state $\hat{z}$ and the parameters of the NAC function, a key aspect that is not directly ablated is the *mechanism* by which "coverage" is quantified from the neuron states. The paper defines NAC based on the *probability density* of $\hat{z}$ states in the InD training data (Equation 4). This density-based approach is central to the concept of "coverage" as used in system testing (where coverage relates to how frequently code paths/states are exercised).

A significant missing ablation would be to replace this density-based coverage measure with alternative, perhaps simpler, measures of typicality or coverage within the $\hat{z}$ state space. For instance, instead of estimating the PDF, one could measure the distance of a test sample's $\hat{z}$ state to the nearest $\hat{z}$ state in the InD training set, or to the centroid of the InD $\hat{z}$ states. These are common approaches in distance-based OOD detection methods (like KNN or Mahalanobis distance) and could serve as alternative ways to quantify how "covered" or "typical" a neuron state is with respect to the InD distribution. Ablating the density estimation component would directly test whether the specific PDF-based approach is superior to other ways of measuring typicality in the $\hat{z}$ space. This is ranked as the most important missing ablation as it questions the core definition of NAC itself.

A second important missing ablation relates to the specific form of the neuron activation state $\hat{z} = \sigma(\mathbf{z} \odot \frac{\partial D\_{\text{KL}}}{\partial \mathbf{z}})$. While the paper ablates the components $\mathbf{z}$ and $\frac{\partial D\_{\text{KL}}}{\partial \mathbf{z}}$, it does not ablate the sigmoid function $\sigma$ or the element-wise product $\odot$. The parameter analysis shows that the steepness $\alpha$ of the sigmoid is important, suggesting the non-linearity plays a role. Removing the sigmoid entirely would test whether this non-linearity is essential or if the raw element-wise product $\mathbf{z} \odot \frac{\partial D\_{\text{KL}}}{\partial \mathbf{z}}$ is sufficient. This is ranked as the second most important missing ablation as it probes the specific mathematical form of the proposed neuron state.

Based on this analysis, I propose the following two missing ablation studies, ranked by importance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablate PDF-based NAC
- **Ablated Part**: Calculation of Neuron Activation Coverage (NAC) using Probability Density Function (PDF) estimation of neuron states over InD data.
- **Action**: REPLACE
- **Replacement**: 
  - Measure typicality by distance to nearest neighbor in InD states
  - Measure typicality by distance to centroid of InD states
- **Metrics**: FPR95, AUROC, Spearman Rank Correlation, OOD Test Accuracy

### Ablate Sigmoid in Neuron State
- **Ablated Part**: Sigmoid activation function in the neuron activation state formulation.
- **Action**: REMOVE
- **Metrics**: FPR95, AUROC, Spearman Rank Correlation, OOD Test Accuracy

</div>