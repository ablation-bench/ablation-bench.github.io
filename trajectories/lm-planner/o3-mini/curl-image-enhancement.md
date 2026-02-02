<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/curl-image-enhancement

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies targeting key components of CURL. The most critical aspect is the multi‐colour space design in the neural curve layers. In the first study we replace the full multi‐colour space block with single colour space processing (e.g. using only RGB, only HSV, or only CIELab) to assess if the benefits arise from exploiting complementary colour representations. Next, we investigate the effect of the ordering of the sequential neural curve layers by reordering the Lab, RGB and HSV adjustments, since the paper finds a specific sequence optimal. Third, we study the backbone’s multi‐scale contextual awareness (MSCA) skip connection within the TED network. By removing these special skip connections and reverting to the standard U-Net skip design, we can verify the contribution of context fusion to enhancing local details. In addition, we target the loss function by removing the curve regularization term (which penalizes curvature and enforces smoothness in the piecewise linear functions) to assess its role in preventing overfitting and color artefacts. Finally, we ablate the cosine similarity term in the RGB loss component, which is intended to enforce vector alignment between predicted and target RGB pixels, to understand its impact on color accuracy. These experiments, evaluated using objective quality metrics (PSNR, SSIM, and additional perceptual/color fidelity measures), will help ascertain the importance of each component.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Single Colour Space Adjustment
- **Ablated Part**: Multi-colour space neural curve layers in the CURL block
- **Action**: REPLACE
- **Replacement**: 
  - Only RGB
  - Only HSV
  - Only CIELab
- **Metrics**: PSNR, SSIM

### Colour Space Order Variation
- **Ablated Part**: Ordering of sequential neural curve layers in the CURL block
- **Action**: REPLACE
- **Replacement**: 
  - Lab -> RGB -> HSV
  - RGB -> HSV -> Lab
  - HSV -> Lab -> RGB
- **Metrics**: PSNR, SSIM

### MSCA-skip Connection Removal
- **Ablated Part**: Multi-scale contextual awareness (MSCA) skip connection in the TED backbone
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, # Parameters

### Curve Regularization Loss Removal
- **Ablated Part**: Curve regularization term in the CURL loss function
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, Color Fidelity

### RGB Loss Cosine Term Removal
- **Ablated Part**: Cosine similarity term in the RGB loss component
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, Color Accuracy

</div>