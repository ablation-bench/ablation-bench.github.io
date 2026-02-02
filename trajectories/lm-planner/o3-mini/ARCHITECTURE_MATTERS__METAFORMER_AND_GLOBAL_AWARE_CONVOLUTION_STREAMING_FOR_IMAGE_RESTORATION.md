<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/ARCHITECTURE_MATTERS__METAFORMER_AND_GLOBAL_AWARE_CONVOLUTION_STREAMING_FOR_IMAGE_RESTORATION

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on a detailed review of the paper, two key components lack standalone ablation studies. First, while the authors introduce the F2C1 module that leverages Fourier transform for global feature transformation, the paper does not isolate the contribution of the Fourier transform itself. A missing ablation here is to remove or replace the Fourier component with other global modeling alternatives (e.g. plain convolution streaming, global average pooling, or self-attention) to evaluate how much the Fourier transform specifically helps in capturing long-range dependencies. Second, the convolution streaming approach employs fixed kernel sizes (e.g., a 7×7 depth-wise convolution in Conv171) to approximate self-attention. This design choice has not been ablated to explore if other kernel sizes could yield a better trade-off between local detail capture and global context. Investigating different kernel sizes (such as 3×3, 5×5, or 9×9) will help quantify how sensitive the model’s performance is to the chosen receptive field in these modules.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Fourier Module Ablation
- **Ablated Part**: The Fourier transform based global feature transformation in the F2C1 module
- **Action**: REPLACE
- **Replacement**: 
  - Remove Fourier transform (i.e., use plain convolution streaming)
  - Replace with global average pooling
  - Replace with self-attention based global module
- **Metrics**: PSNR, SSIM, MACs, Params

### Kernel Size Ablation in Convolution Streaming
- **Ablated Part**: The depth-wise convolution kernel size in the convolution streaming blocks (e.g., Conv171/Conv1311)
- **Action**: REPLACE
- **Replacement**: 
  - 3x3
  - 5x5
  - 7x7 (baseline)
  - 9x9
- **Metrics**: PSNR, SSIM

</div>