<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/MaGIC__Multi_modality_Guided_Image_Completion

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The MaGIC paper presents two core components: the modality-specific conditional U-Net (MCU-Net) for injecting guidance and the Consistent Modality Blending (CMB) technique for multi-modal integration. While the paper conducts several ablations—such as evaluating the impact of different modalities, hyperparameter choices (e.g., the number of guidance steps P and iteration Q in CMB), and even comparing a naive feature-level addition (FLA) with the CMB approach—it does not investigate alternative design choices for two essential components. First, the injection method in MCU-Net simply adds the encoded guidance signal (F l^c) to the intermediate encoder features (F l_enc). It would be valuable to study alternative guidance fusion strategies such as concatenation with a subsequent 1×1 convolution, FiLM modulation, or attention-based fusion to determine which method yields superior performance on completed image quality metrics (e.g., FID, PickScore, U-IDS, and P-IDS). Second, in the CMB module the loss function is formulated as an L2 (Euclidean) distance between the guidance features and the original features. Exploring other loss functions—such as an L1 norm or cosine similarity—may provide different trade-offs between preserving fine details and ensuring robustness when blending guidance signals. These ablations would offer further insights into the design choices of MaGIC and whether alternative strategies could enhance its performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Guidance Injection Fusion
- **Ablated Part**: The mechanism for injecting modality guidance signals into the U-Net denoiser (currently using simple feature addition in MCU-Net)
- **Action**: REPLACE
- **Replacement**: 
  - concatenation followed by a 1x1 convolution
  - FiLM modulation
  - attention-based fusion
- **Metrics**: FID, PickScore, U-IDS, P-IDS

### Ablation on Guidance Loss Function
- **Ablated Part**: The energy loss function used for consistent modality blending in the CMB module (currently an L2 Euclidean distance)
- **Action**: REPLACE
- **Replacement**: 
  - L1 norm
  - cosine similarity
- **Metrics**: FID, PickScore, U-IDS, P-IDS

</div>