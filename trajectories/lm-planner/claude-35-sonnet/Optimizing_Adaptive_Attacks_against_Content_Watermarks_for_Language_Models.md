<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Optimizing_Adaptive_Attacks_against_Content_Watermarks_for_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a method to optimize adaptive attacks against content watermarks for LLMs. The key components of their method are:

1. Using preference-based optimization to tune attacks against known watermarking methods
2. Curating preference datasets using LLMs to adaptively fine-tune watermark evasion attacks
3. Using surrogate models and keys to overcome uncertainty about the provider's watermarking key

The paper already includes ablations on:
- Adaptivity (adaptive vs non-adaptive settings)
- Target model sizes (Llama2-13b, Llama3-70b)
- Attacker model sizes (0.5b to 7b parameters)
- Different watermarking methods
- Hyper-parameters like FPR thresholds

However, there are two important missing ablations that would provide better insights:

1. The impact of the preference dataset size on attack effectiveness. The paper uses 7,000 samples but doesn't analyze how the dataset size affects performance.

2. The effect of different surrogate model architectures. While they test different sizes, they don't ablate over fundamentally different architectures (e.g., decoder-only vs encoder-decoder) which could impact the attack's effectiveness.

These ablations would help better understand the method's sensitivity to these important design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Dataset Size Ablation
- **Ablated Part**: preference dataset size for training
- **Action**: REPLACE
- **Replacement**: 
  - 1000
  - 3000
  - 5000
  - 10000
  - 15000
- **Metrics**: evasion_rate, text_quality, LLM-Judge, MAUVE

### Architecture Ablation
- **Ablated Part**: surrogate model architecture
- **Action**: REPLACE
- **Replacement**: 
  - T5
  - BART
  - GPT-Neo
  - OPT
- **Metrics**: evasion_rate, text_quality, LLM-Judge, MAUVE

</div>