<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Neuron_Activation_Coverage__Rethinking_Out_of_distribution_Detection_and_Generalization

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One key component of NAC is the way in which the probability density function (PDF) of the neuron activation states is estimated from the in‐distribution data. In the paper, a simple histogram‐based approach is adopted to approximate the PDF and then used to compute the coverage scores. However, the choice of PDF approximation may have a significant impact on the reliability of the computed NAC values – and thus on OOD detection and generalization performance. An ablation study that replaces the histogram‐based approach with alternative PDF estimation methods (e.g., kernel density estimation or a parametric model such as a Gaussian mixture model) would provide important insights into whether the current simple method is optimal or if improvements can be achieved with more refined statistical modeling.

Another important design decision is that during the construction of the NAC function the authors choose to use only training samples that have been correctly classified in order to reduce noise. While this is intuitively reasonable, it is not clear how much performance would degrade if misclassified (and potentially noisy) samples were included in the computation of the neuron activation distribution. An ablation study that “removes” this filtering – in other words, that uses all available training data – would assess the importance of utilizing only correctly classified samples, and help quantify the robustness of the proposed coverage criterion when faced with label errors or ambiguous samples.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: PDF Approximation Method
- **Ablated Part**: the histogram-based PDF estimation used for constructing the NAC function
- **Action**: REPLACE
- **Replacement**: 
  - Kernel Density Estimation
  - Gaussian Mixture Model
- **Metrics**: FPR95, AUROC, Rank Correlation, OOD Test Accuracy

### Ablation: Inclusion of Misclassified Samples
- **Ablated Part**: the filtering mechanism that excludes misclassified training samples during NAC construction
- **Action**: REMOVE
- **Metrics**: FPR95, AUROC, Rank Correlation, OOD Test Accuracy

</div>