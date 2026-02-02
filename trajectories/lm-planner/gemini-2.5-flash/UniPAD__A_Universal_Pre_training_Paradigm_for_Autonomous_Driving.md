<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/UniPAD__A_Universal_Pre_training_Paradigm_for_Autonomous_Driving

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants to identify up to two important missing ablation studies for the UniPAD paper. I have read the paper, focusing on the method description (Section 3) and the existing ablation studies (Section 4.6).

UniPAD's core idea is a self-supervised pre-training paradigm using 3D volumetric differentiable rendering, unifying 2D and 3D modalities into a 3D voxel space. Key components include the modal-specific encoder, the unified 3D volumetric representation, the neural rendering decoder, memory-friendly ray sampling, and the pre-training loss.

The paper already includes ablations on:
- Masking ratio (for camera modality)
- Rendering decoder depth and width
- Rendering technique (UniSurf, VolSDF, NeuS)
- Ray sampling strategy (Dilation, Random, Depth-aware)
- Feature projection layer within the 3D volume representation
- Contribution of pre-trained components (Encoder, FPN, VT)

Based on the method's description and the existing ablations, two important aspects that are not fully explored through ablation are:

1.  **The resolution of the unified 3D volumetric representation:** The paper states a uniform voxel representation with the shape of 180x180x5 is constructed across modalities. This is a crucial hyperparameter defining the spatial granularity and extent of the 3D space representation. While the feature projection layer *onto* this volume is ablated, the impact of the volume's resolution itself is not investigated. Different resolutions would affect the capacity to represent fine-grained details versus the computational cost and memory footprint. Ablating this would show the sensitivity of the method to this core design choice.

2.  **The contribution of the individual loss components (Color vs. Depth):** The pre-training loss is a combination of color loss and depth loss with fixed weights (λRGB=10, λdepth=10). The differentiable rendering decoder reconstructs both RGB and depth. It's important to understand the relative importance of reconstructing geometry (depth) versus appearance (color) for the downstream tasks. Ablating the loss weights or using only one loss component would clarify their individual contributions to the learned representation's effectiveness.

I will propose these two as the missing ablation studies. The metrics used in the paper's ablation studies are primarily NDS and mAP for 3D object detection, which is a major downstream task evaluated. I will use these metrics for the proposed ablations.

Ranking: The resolution of the 3D volume feels slightly more fundamental to the "unified 3D volumetric representation" concept than the specific balance of the rendering losses, although both are critical. I will rank the volume resolution ablation first.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on 3D Volume Resolution
- **Ablated Part**: Resolution of the unified 3D volumetric representation
- **Action**: REPLACE
- **Replacement**: 
  - 90x90x5
  - 180x180x3
  - 240x240x5
- **Metrics**: NDS, mAP

### Ablation on Pre-training Loss Weights
- **Ablated Part**: Weights of the color and depth loss components in the pre-training loss
- **Action**: REPLACE
- **Replacement**: 
  - lambda_RGB=10, lambda_depth=0
  - lambda_RGB=0, lambda_depth=10
  - lambda_RGB=5, lambda_depth=5
- **Metrics**: NDS, mAP

</div>