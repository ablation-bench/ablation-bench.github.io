<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Layer_Swapping_for_Zero_Shot_Cross_Lingual_Transfer_in_Large_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents a promising layer swapping method for zero‐shot cross‐lingual transfer by merging math and language experts. However, two important ablations are missing. First, the methodology relies on experts that have been fine‐tuned only lightly; it remains unclear how well the method holds up if the experts diverge more significantly (e.g. due to extended fine‐tuning or higher learning rates). Such divergence may lead to misalignment in latent representations, thereby undermining the benefits of layer swapping. An ablation study that replaces the existing fine‐tuning configuration with schedules that induce varying levels of divergence would reveal the robustness (or fragility) of the layer swapping method. Second, while the paper uses full fine‐tuning for both experts, the discussion mentions potential benefits of parameter‐efficient methods (e.g. LoRA) to further modularize and reduce interference. An ablation study that replaces full SFT with adapter-based fine-tuning techniques would help determine if the benefits of layer swapping transfer when using such low-rank or adapter-based methods. These experiments would provide valuable insights into the method’s dependence on expert similarity and the generalizability of layer swapping across fine-tuning regimes.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Expert Divergence Ablation
- **Ablated Part**: The degree of divergence between the math and language experts due to extended fine-tuning (e.g., longer training duration or higher learning rates) before layer swapping
- **Action**: REPLACE
- **Replacement**: 
  - extended fine-tuning duration
  - increased learning rate settings
  - longer SFT runs
- **Metrics**: MGSM, BELEBELE, FLORES, MBPP, MMLU

### Parameter-Efficient Fine-Tuning Ablation
- **Ablated Part**: The full fine-tuning paradigm used to produce the experts, replaced by parameter-efficient methods (e.g., LoRA, AdapterFusion)
- **Action**: REPLACE
- **Replacement**: 
  - LoRA
  - AdapterFusion
  - Prefix Tuning
- **Metrics**: MGSM, BELEBELE, FLORES, MBPP, MMLU

</div>