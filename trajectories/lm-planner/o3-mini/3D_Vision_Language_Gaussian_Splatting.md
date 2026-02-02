<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/3D_Vision_Language_Gaussian_Splatting

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The provided paper already conducts various ablation studies on the key components of the proposed method – such as different fusion strategies, the design of the semantic indicator versus using color opacity, as well as variations in the camera view blending module and the interpolation ratio. However, two important aspects remain unexplored. First, the overall objective (Eq. 12) balances the traditional rasterization losses with the camera-view blending loss via a trade-off parameter λ (set to 1.2 in the experiments). The sensitivity of the final performance (e.g., in terms of mIoU and localization accuracy) to different choices of λ is not examined. Ablating this weighting parameter could provide insights into the relative importance of the blending loss versus the standard reconstruction losses. Second, although the paper leverages pre-trained vision-language models (SAM for segmentation and OpenCLIP for language embeddings) to extract ground-truth semantic features, it does not study how the method’s performance varies when different vision-language models are used. Since the quality of extracted semantic features is critical for robust 3D scene understanding, evaluating alternative vision-language backbones (e.g., larger or different architectures such as OpenCLIP ViT-L/14, ALIGN, or FLAVA) could be highly informative.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Blending Loss Weight Ablation
- **Ablated Part**: The trade-off parameter λ that balances the rasterization loss and the camera-view blending loss in the overall optimization objective
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.5
  - 1.0
  - 1.2
  - 2.0
- **Metrics**: mIoU, Localization Accuracy

### Vision-Language Feature Extractor Ablation
- **Ablated Part**: The pre-trained vision-language model used for extracting language features (i.e., the semantic ground-truth representations)
- **Action**: REPLACE
- **Replacement**: 
  - OpenCLIP ViT-B/16
  - OpenCLIP ViT-L/14
  - ALIGN
  - FLAVA
- **Metrics**: mIoU, Localization Accuracy

</div>