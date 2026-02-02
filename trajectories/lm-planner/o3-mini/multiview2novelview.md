<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/multiview2novelview

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies that target the major components of the framework. The first study removes the self-learned confidence aggregation mechanism to measure its importance in merging the flow predictor and pixel generator outputs – we hypothesize that without adaptive weighting the aggregated prediction will suffer, which should reflect in worse L1, PSNR, and SSIM scores. Next, we individually remove each of the two prediction modules: first, by removing the pixel generator (which hallucinates missing pixels) to rely solely on the flow predictor, and then by removing the flow predictor (which warps pixels from the source) so that only the pixel generator contributes. These studies reveal how complementary these modules are for structurally consistent and sharp output. Furthermore, we target the recurrent nature of the pixel generator by replacing its ConvLSTM-based bottleneck with a standard feed-forward convolutional network (or a variant with dilated convolutions) to evaluate the benefit of iterative refinement. Finally, we ablate the adversarial loss in the pixel generator training to see how important the adversarial supervision is for producing sharp, realistic images. Metrics such as L1 reconstruction error, PSNR, SSIM, and (for the adversarial study) FID will be used consistently to quantify the quality of the synthesized images.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Remove Confidence Aggregation
- **Ablated Part**: Self-learned confidence aggregation mechanism used for merging the outputs from the flow predictor and pixel generator
- **Action**: REMOVE
- **Metrics**: L1 reconstruction, PSNR, SSIM

### Ablation 2: Remove Pixel Generator
- **Ablated Part**: Pixel generator module responsible for hallucinating missing pixels and refining the synthesis
- **Action**: REMOVE
- **Metrics**: L1 reconstruction, PSNR, SSIM

### Ablation 3: Remove Flow Predictor
- **Ablated Part**: Flow predictor module that warps source image pixels based on predicted flow fields
- **Action**: REMOVE
- **Metrics**: L1 reconstruction, PSNR, SSIM

### Ablation 4: Replace Recurrent Component in Pixel Generator
- **Ablated Part**: ConvLSTM-based recurrent module in the pixel generator responsible for progressive refinement
- **Action**: REPLACE
- **Replacement**: 
  - Standard feed-forward CNN
  - Dilated convolution variant
- **Metrics**: L1 reconstruction, PSNR, SSIM

### Ablation 5: Remove Adversarial Loss
- **Ablated Part**: Adversarial loss component in the pixel generator training that enforces image sharpness
- **Action**: REMOVE
- **Metrics**: L1 reconstruction, PSNR, SSIM, FID

</div>