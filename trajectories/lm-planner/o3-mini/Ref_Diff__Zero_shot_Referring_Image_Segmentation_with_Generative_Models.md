<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Ref_Diff__Zero_shot_Referring_Image_Segmentation_with_Generative_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, the authors provide several ablation studies demonstrating the contributions of using different modules (segmentor, generative process, discriminative process) and various design choices such as the weighting parameter α and the attention token selection. However, two important experiments seem to be missing. First, the noise level parameter (t) in the generative process—which is used to generate the noised image state xᵗ—has been fixed (t=2) without a sensitivity analysis; such an ablation would reveal how the amount of injected noise impacts the quality of the attention maps and, ultimately, the segmentation accuracy measured by mIoU and oIoU. Second, while the paper leverages Stable Diffusion as the generative model, it remains unclear whether the overall performance advantage is specific to this choice. An ablation study that replaces the generative model with alternative state-of-the-art models (e.g., DALL-E 2, Imagen) would help assess if the improvements are due to the properties of generative models in general, or if they specifically hinge on Stable Diffusion.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Noise Level Sensitivity
- **Ablated Part**: Gaussian noise addition in the generative process (parameter t)
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 2
  - 3
  - 4
  - 5
- **Metrics**: mIoU, oIoU

### Ablation: Alternative Generative Models
- **Ablated Part**: Generative model used for extracting attention and generating proposals
- **Action**: REPLACE
- **Replacement**: 
  - Stable Diffusion V1.5
  - DALL-E 2
  - Imagen
- **Metrics**: mIoU, oIoU

</div>