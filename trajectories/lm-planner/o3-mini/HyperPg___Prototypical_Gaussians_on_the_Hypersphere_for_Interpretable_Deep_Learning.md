<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/HyperPg___Prototypical_Gaussians_on_the_Hypersphere_for_Interpretable_Deep_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One important novelty of HyperPg is its use of learnable variance (σ) in representing the uncertainty of cosine similarity scores. However, the paper does not report an ablation study that examines the impact of making σ learnable versus fixing it to a constant. By replacing the learnable standard deviation with fixed constant values, one can study how much the dynamic adaptation of the Gaussian’s spread on the hypersphere contributes to classification performance and interpretability. Another potential missing ablation is to assess the choice of cosine similarity within the HyperPg module. Although the paper exploits the cosine similarity for projecting latent vectors on the hypersphere, it would be interesting to replace it with an alternative similarity metric (such as an L2-based distance measure) to evaluate if the probabilistic modeling of similarity scores is sensitive to the underlying similarity function. These experiments would provide further insight into the critical role of model components in HyperPg.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Fixed Variance Ablation
- **Ablated Part**: Learnable standard deviation (variance) parameter in the HyperPg prototype module
- **Action**: REPLACE
- **Replacement**: 
  - constant σ = 0.05
  - constant σ = 0.1
  - constant σ = 0.2
- **Metrics**: CUB Top-1 Accuracy, CARS Top-1 Accuracy, Training Convergence (Epochs), Qualitative Interpretability

### Similarity Measure Ablation
- **Ablated Part**: Cosine similarity computation in the HyperPg module
- **Action**: REPLACE
- **Replacement**: 
  - Euclidean distance
  - L2 distance
  - Normalized Euclidean distance
- **Metrics**: CUB Top-1 Accuracy, CARS Top-1 Accuracy, Training Convergence (Epochs), Qualitative Interpretability

</div>