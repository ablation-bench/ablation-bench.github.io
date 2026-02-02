<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Should_VLMs_be_Pre_trained_with_Image_Data_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We examined the paper and noted that a wide variety of ablations have been conducted regarding the pre-training phase (percentage of text-only pre-training, image-to-text ratios, training from scratch vs. from a checkpoint, use of different datasets, and freezing vs. unfreezing the image encoder). However, missing from the study is an investigation into (1) the effect of the ordering of image and text tokens within the input sequence – the paper always places the image tokens before the text tokens, yet alternative ordering schemes (such as interleaving or having text tokens first) might affect the learning dynamics and downstream performance; and (2) the impact of using a bidirectional (PrefixLM-style) image encoding strategy rather than the conventional unidirectional setting. The paper explicitly mentions that they do not use a PrefixLM architecture despite its potential benefits. Investigating these changes can shed light on the importance of sequence organization and encoding design for multi-modal integration.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Input Token Ordering
- **Ablated Part**: Ordering of image and text tokens in the input sequence
- **Action**: REPLACE
- **Replacement**: 
  - Image tokens first then text tokens
  - Interleaved image and text tokens
  - Text tokens first then image tokens
- **Metrics**: Vision Stable Score, Text Stable Score, VQA-v2, ARC-easy

### Ablation: PrefixLM for Image Encoding
- **Ablated Part**: Image encoding strategy, comparing standard unidirectional encoding with a bidirectional PrefixLM approach
- **Action**: REPLACE
- **Replacement**: 
  - Standard unidirectional image-first encoding
  - PrefixLM-based bidirectional image encoding
- **Metrics**: Vision Stable Score, Text Stable Score, VQA-v2, ARC-easy

</div>