<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Shh__don_t_say_that__Domain_Certification_in_LLMs

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes VALID, a method for domain certification in LLMs that uses rejection sampling with a guide model G to provide adversarial bounds on out-of-domain responses.

The paper already includes several ablation studies:
1. Analysis of different guide model sizes (GXS, GS, G) in Appendix G.2
2. Comparison between guide model G and base model L performance in Appendix G.1
3. Analysis of different numbers of sampling iterations T in Appendix F

However, there are two important ablation studies missing that could provide valuable insights:

1. The most critical missing ablation is on the choice of the guide model architecture. The paper uses GPT-2 style models but doesn't explore how different architectures (e.g., encoder-decoder vs decoder-only) might affect certification performance.

2. The second important missing ablation is on the training data composition for the guide model G. The paper trains G on in-domain data but doesn't explore how including different ratios of out-of-domain data in G's training might improve its ability to distinguish domains.

These ablations would help understand key design choices in implementing VALID.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Guide Model Architecture Ablation
- **Ablated Part**: Architecture of the guide model G
- **Action**: REPLACE
- **Replacement**: 
  - GPT-2 (decoder-only)
  - T5 (encoder-decoder)
  - BERT (encoder-only)
- **Metrics**: False Rejection Rate, Domain Certificate ε, Constriction Ratio

### Guide Model Training Data Ablation
- **Ablated Part**: Training data composition for guide model G
- **Action**: REPLACE
- **Replacement**: 
  - 100% in-domain
  - 90% in-domain + 10% OOD
  - 80% in-domain + 20% OOD
- **Metrics**: False Rejection Rate, Domain Certificate ε, Constriction Ratio

</div>