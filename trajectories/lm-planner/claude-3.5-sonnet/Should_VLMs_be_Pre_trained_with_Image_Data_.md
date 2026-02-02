<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Should_VLMs_be_Pre_trained_with_Image_Data_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper investigates when and how to introduce visual data during language model training. The authors already conduct several key ablations including:

1. Impact of amount of text-only pre-training before introducing images
2. Impact of image-to-text ratio during pre-training 
3. Effect of fine-tuning epochs
4. Effect of introducing images from scratch vs after pre-training
5. Effect of instruction tuning data during pre-training
6. Effect of freezing vs unfreezing image encoder weights
7. Effect of different image datasets and encoders

However, there are two important ablations that appear to be missing:

1. The effect of the projection block architecture between the image encoder and language model. The paper uses a simple 2-layer MLP but doesn't explore alternatives. This is a critical component for bridging the visual and language modalities.

2. The effect of image token sequence length (currently fixed at 729 tokens). This is an important hyperparameter that affects both computational cost and model performance, as it determines how much visual information is passed to the language model.

These ablations would provide valuable insights into the architectural choices for vision-language integration.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Projection Architecture Ablation
- **Ablated Part**: 2-layer MLP projection block between image encoder and language model
- **Action**: REPLACE
- **Replacement**: 
  - 4-layer MLP
  - Transformer layers
  - Cross-attention layers
- **Metrics**: VQAv2, GQA, TextVQA, RefCOCO, OCID, POPE, AGIEval, ARC Easy

### Image Token Length Ablation
- **Ablated Part**: Number of image tokens (currently 729)
- **Action**: REPLACE
- **Replacement**: 
  - 256
  - 512
  - 1024
  - 1536
- **Metrics**: VQAv2, GQA, TextVQA, RefCOCO, OCID, POPE, AGIEval, ARC Easy

</div>