<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/curl-image-enhancement

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "CURL: Neural Curve Layers for Global Image Enhancement" proposes a novel method for image enhancement consisting of a backbone network (TED) for local adjustments and a CURL block for global adjustments using learned neural curves in multiple color spaces (Lab, RGB, HSV), guided by a multi-color space loss function.

To understand the contribution of the key components of the CURL method, I propose a set of ablation studies. The most critical components to investigate are:
1.  **The CURL block itself:** Is the global adjustment block necessary, or is the TED backbone sufficient?
2.  **The multi-color space approach:** Does processing the image sequentially in different color spaces (Lab, RGB, HSV) contribute to the performance?
3.  **The multi-color space loss function:** How do the different terms of the novel loss function contribute to the final image quality?
4.  **The ordering of color spaces:** The paper mentions optimizing the sequence of color spaces (Lab -> RGB -> HSV). How does changing this order affect results?
5.  **The MSCA skip connection in the TED backbone:** The paper claims the MSCA skip connection improves performance over a standard U-Net skip. Quantifying this difference is important.

Based on this analysis, I've selected and prioritized five ablation studies focusing on these key aspects. The metrics chosen (PSNR, SSIM, LPIPS, MS-SSIM) are standard for image quality assessment and are used within the paper's evaluation. For the backbone ablation, the number of parameters is also a relevant metric as discussed in the paper.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablate CURL Block
- **Ablated Part**: The entire CURL global image adjustment block
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, LPIPS, MS-SSIM

### Ablate Color Spaces in CURL
- **Ablated Part**: Using multiple color spaces (Lab, RGB, HSV) sequentially in the CURL block
- **Action**: REPLACE
- **Replacement**: 
  - Lab only
  - RGB only
  - HSV only
- **Metrics**: PSNR, SSIM, LPIPS, MS-SSIM

### Ablate Loss Function Terms
- **Ablated Part**: The full multi-color space loss function
- **Action**: REPLACE
- **Replacement**: 
  - L1/L2 RGB only
  - L1/L2 RGB + Lab (L1+MS-SSIM)
  - L1/L2 RGB + HSV (L1)
  - L1/L2 RGB + Lab + HSV (no Reg)
  - Full Loss
- **Metrics**: PSNR, SSIM, LPIPS, MS-SSIM

### Ablate Color Space Ordering
- **Ablated Part**: The specific order of color spaces (Lab -> RGB -> HSV) in the CURL block
- **Action**: REPLACE
- **Replacement**: 
  - RGB -> Lab -> HSV
  - HSV -> Lab -> RGB
- **Metrics**: PSNR, SSIM, LPIPS, MS-SSIM

### Ablate MSCA Skip Connection
- **Ablated Part**: The Multi-Scale Contextual Awareness (MSCA) design of the skip connection at level 1 in the TED backbone
- **Action**: REPLACE
- **Replacement**: 
  - Standard U-Net skip connection (concatenation)
- **Metrics**: PSNR, SSIM, LPIPS, MS-SSIM, # Parameters

</div>