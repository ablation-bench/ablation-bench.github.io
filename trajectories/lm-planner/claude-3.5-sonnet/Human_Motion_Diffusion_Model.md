<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Human_Motion_Diffusion_Model

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that the authors have already conducted several ablation studies:
1. Different architectures (Transformer encoder, decoder, GRU, U-net)
2. Different number of diffusion steps (T=10,100,500,1000)
3. Geometric losses combinations (foot contact, velocity, pose)

However, there are two critical missing ablation studies that could provide important insights:

1. The most important missing ablation is on the choice of predicting the clean sample x̂0 directly instead of predicting the noise ε as done in most diffusion models. This is a key design choice mentioned in the abstract and method section, but its impact is never quantified.

2. The second important missing ablation is on the classifier-free guidance scale s. While they mention using s=2.5 and show a brief plot in Fig 4b, a systematic ablation comparing different guidance strategies (classifier-free vs classifier-based) would be valuable since this affects the diversity-fidelity tradeoff.

I rank these in this order because the first one is a fundamental architectural choice that differentiates this work, while the second one is more of a hyperparameter choice, though still important.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Clean Sample vs Noise Prediction
- **Ablated Part**: The model's prediction target (currently predicting clean sample x̂0)
- **Action**: REPLACE
- **Replacement**: 
  - noise prediction ε
  - mixed prediction (both x̂0 and ε)
- **Metrics**: FID, R-precision, Multimodal-Dist, Diversity

### Guidance Strategy Comparison
- **Ablated Part**: Classifier-free guidance approach
- **Action**: REPLACE
- **Replacement**: 
  - classifier-based guidance
  - no guidance
  - classifier-free with s=[1.0, 1.5, 2.0, 3.0, 3.5]
- **Metrics**: FID, R-precision, Diversity, Multimodality

</div>