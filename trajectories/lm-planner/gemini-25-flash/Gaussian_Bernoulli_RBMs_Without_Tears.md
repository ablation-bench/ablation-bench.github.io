<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Gaussian_Bernoulli_RBMs_Without_Tears

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Gaussian-Bernoulli RBMs Without Tears" introduces two main innovations: a novel Gibbs-Langevin sampling algorithm and a modified Contrastive Divergence (CD) algorithm that starts the negative phase from noise. It also highlights the importance of learning per-visible-unit variances and using gradient clipping for robust training with large learning rates, contrasting with previous work that required various tricks.

The paper includes an ablation study in Appendix B.2 on MNIST, investigating the effect of CD steps, hidden size, Langevin steps, Langevin step size, annealing, Metropolis adjustment steps, and the initialization source (data vs. noise) for the negative chain.

Based on the paper's claims and the existing ablations, two important missing ablation studies are:

1.  **Gradient Clipping:** The authors state that gradient clipping, along with modified CD, is *sufficient* for robust training with large learning rates. While they use gradient clipping (norm 10) in all experiments, they do not present an ablation study that removes or varies the gradient clipping to demonstrate its necessity or impact on training stability and performance, especially when using a large learning rate (0.01). This is a key claim about their training methodology's robustness.
2.  **Learning Variances:** The paper emphasizes that their method successfully learns low per-visible-unit variances, which is challenging and often avoided in prior work by fixing variances. However, the paper does not include an ablation comparing the performance of their method when learning variances versus fixing them to a constant value (a common practice in the literature). This ablation would quantify the benefit of learning variances within their proposed framework.

These two ablations are crucial for understanding the contribution and necessity of gradient clipping for training stability and the impact of learning variances on the model's generative performance, both of which are significant aspects discussed in the paper. The primary quantitative metric used for evaluating image generation quality in the paper is FID, making it the most relevant metric for these suggested ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Gradient Clipping
- **Ablated Part**: Gradient clipping during training
- **Action**: REMOVE
- **Metrics**: FID

### Ablation: Learned Variances
- **Ablated Part**: Learning per-visible-unit variances
- **Action**: REPLACE
- **Replacement**: 
  - Fixed variance (e.g., 1.0)
- **Metrics**: FID

</div>