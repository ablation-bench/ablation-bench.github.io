<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Black_Sheep_in_the_Herd__Playing_with_Spuriously_Correlated_Attributes_for_Vision_Language_Recognition

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces two main components: SAP (Spurious Attribute Probing) and SAS (Spurious Attribute Shielding). Looking at the existing ablations in the paper:

1. The paper already ablates:
- Different number of SD prompts for image generation
- Different threshold values (γ) for spurious attribute selection
- Different balancing weights (λ) between main and subsidiary tasks
- Different methods for constructing pseudo categories (masking vs inpainting vs synthesis)

2. However, I notice two important missing ablations:

First, while the paper uses MLLMs (specifically GPT-4V) to identify spurious attributes, there's no systematic ablation of the MLLM component's role in attribute identification. While Section B.4 briefly compares different MLLMs, it doesn't examine how the quality of spurious attribute identification affects the final performance.

Second, while SAS introduces a subsidiary task with pseudo categories, there's no ablation studying how the number of pseudo categories per spurious attribute affects performance. The paper fixes this to match the number of shots in the target category (16), but this choice isn't validated through ablation.

These missing ablations would help understand the robustness and sensitivity of the method to its key components.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### MLLM Quality Ablation
- **Ablated Part**: MLLM component for spurious attribute identification
- **Action**: REPLACE
- **Replacement**: 
  - GPT-4V
  - BLIP-2
  - LLaVA
  - InternVL
  - No MLLM (random attribute selection)
- **Metrics**: base accuracy, new accuracy, harmonic mean

### Pseudo Categories Scale Ablation
- **Ablated Part**: number of pseudo categories per spurious attribute
- **Action**: REPLACE
- **Replacement**: 
  - 4
  - 8
  - 16
  - 32
  - 64
- **Metrics**: base accuracy, new accuracy, harmonic mean

</div>