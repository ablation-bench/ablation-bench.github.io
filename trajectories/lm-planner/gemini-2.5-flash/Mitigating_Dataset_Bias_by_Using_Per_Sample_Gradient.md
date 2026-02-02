<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Mitigating_Dataset_Bias_by_Using_Per_Sample_Gradient

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Mitigating Dataset Bias by Using Per-Sample Gradient (PGD)" proposes a two-stage debiasing method. The core idea is to train a biased model, use the per-sample gradient norm from this model to determine sampling probabilities, and then train a debiased model using importance sampling based on these probabilities. The paper includes several ablation studies in Section 4.3 and Appendix C, investigating the effect of using Generalized Cross-Entropy (GCE) loss, data augmentation, multi-stage vs single-stage training, resampling vs reweighting, and the choice of gradient norm (L1, L2, L-inf, L2^2).

Based on my analysis, two important aspects of the PGD method are not fully ablated:

1.  **The source of the per-sample gradient:** The paper states that computing the gradient for all samples requires huge resources and memory, so they only extract the gradient of the *final FC layer parameters*. While this is a practical choice, the impact of using only the final layer gradient versus gradients from other layers (e.g., earlier convolutional layers, the feature extractor part) or the full network gradient is not empirically evaluated. The theoretical justification in Section 5 is based on the full model parameters (θ), but the implementation uses a specific subset (θfc). An ablation study on the gradient source would clarify how much performance is gained or lost by this approximation and whether the signal for identifying bias-conflicting samples is indeed concentrated in the final layer gradient.
2.  **Initialization of the debiased model:** Algorithm 1 shows that the debiased model in Step 3 inherits the parameters from the biased model trained in Step 1 (θT<sup>b</sup>). The paper mentions this but does not provide an ablation study comparing this approach to initializing the debiased model with random parameters. Inheriting parameters might provide a better starting point, but it could also potentially carry over some of the bias learned in the first stage. Evaluating the impact of this initialization strategy is important for understanding the training dynamics and final performance.

These two missing ablations are significant because they relate directly to key design choices in the PGD algorithm: what gradient information is used and how the second training stage is initialized. Evaluating these choices would provide stronger empirical support for the method's specific implementation details. I will prioritize these two ablations. The metrics used in the paper's main results tables (average test accuracy, worst-group accuracy where applicable, and standard deviation) should be used for these ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Gradient Source Ablation
- **Ablated Part**: Source of the per-sample gradient used for sampling probability (final FC layer vs other layers/full network)
- **Action**: REPLACE
- **Replacement**: 
  - gradient of feature extractor parameters
  - gradient of all model parameters
- **Metrics**: Average test accuracy, Worst test accuracy, Standard deviation

### Debiased Model Initialization Ablation
- **Ablated Part**: Initialization of the debiased model parameters in Step 3
- **Action**: REPLACE
- **Replacement**: 
  - random initialization
- **Metrics**: Average test accuracy, Worst test accuracy, Standard deviation

</div>