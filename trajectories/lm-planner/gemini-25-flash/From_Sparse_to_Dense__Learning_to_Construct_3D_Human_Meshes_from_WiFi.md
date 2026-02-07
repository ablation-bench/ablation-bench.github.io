<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/From_Sparse_to_Dense__Learning_to_Construct_3D_Human_Meshes_from_WiFi

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "From Sparse to Dense: Learning to Construct 3D Human Meshes from WiFi" introduces WiMTR, a novel Transformer-based model for multi-person mesh regression from WiFi CSI signals. The model consists of four main components: CSI feature extractor, CSI feature encoder, coarse decoder, and refine decoder. The paper also highlights the importance of preprocessing (phase sanitization) and a specific query generation method (differentiation branch) in the refine decoder.

The existing ablation study (Section 4.5) investigates the contribution of:
1.  **Refine Decoder:** Shows performance degradation when removed, confirming its role in refinement.
2.  **Joint Differentiation:** Compares differentiation-based joint queries with randomly initialized ones, demonstrating the benefit of the proposed method.
3.  **Phase Sanitization:** Compares denoised phase, raw phase, and no phase input, highlighting the importance of denoised phase information.

While these ablations cover important aspects, several other key components and design choices are not ablated, which would provide further insight into the model's performance attribution. Two particularly important missing ablations are:

1.  **CSI Feature Encoder Depth:** The CSI Feature Encoder is responsible for extracting global features from the tokenized CSI signals using multiple Transformer layers (stated as 6 layers in Section 3.2). The number of layers in a Transformer encoder is a critical hyperparameter that directly impacts the model's capacity to learn complex representations. An ablation study varying the number of encoder layers would demonstrate how the depth of the encoder contributes to performance and whether the chosen number of layers is optimal or if a simpler/deeper encoder could suffice or perform better. This is a standard and crucial ablation for Transformer-based architectures.

2.  **CSI Tokenization Strategy:** The paper proposes a specific method for tokenizing the 4D CSI signal (3x3x20x60 after preprocessing) by flattening the first three dimensions (3x3x20) into a sequence of 180 tokens, each with a dimension of 60. This is a non-trivial design choice for handling the multi-dimensional CSI data. The paper mentions that others flatten the entire signal. An ablation comparing their chosen tokenization strategy with alternative methods, such as flattening the entire 4D tensor into a single long sequence (10800 tokens), would validate the effectiveness of their specific approach to structuring the input sequence for the Transformer. This is fundamental to how the model perceives the input data.

These two ablations are important because they investigate core architectural choices (encoder depth) and fundamental input processing (tokenization strategy) that are likely to have a significant impact on the model's ability to learn from the sparse CSI data. The metrics used in the paper's existing ablation study (MPJPE, PAMPJPE, PVE) are appropriate for evaluating these proposed ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### CSI Feature Encoder Depth
- **Ablated Part**: Number of layers in the CSI Feature Encoder
- **Action**: REPLACE
- **Replacement**: 
  - 3
  - 4
  - 6
- **Metrics**: MPJPE, PAMPJPE, PVE

### CSI Tokenization Strategy
- **Ablated Part**: Method for tokenizing the 4D CSI signal (3x3x20x60)
- **Action**: REPLACE
- **Replacement**: 
  - Flatten 3x3x20 dimensions (180x60)
  - Flatten all 3x3x20x60 dimensions (10800x1)
- **Metrics**: MPJPE, PAMPJPE, PVE

</div>