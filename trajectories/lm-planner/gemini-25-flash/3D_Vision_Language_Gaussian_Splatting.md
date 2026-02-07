<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/3D_Vision_Language_Gaussian_Splatting

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "3D Vision-Language Gaussian Splatting" proposes a novel method for multi-modal 3D scene understanding using Gaussian Splatting. The key contributions are a cross-modal rasterizer with modality fusion and a smoothed semantic indicator, and a camera-view blending technique for semantic regularization.

The paper includes several ablation studies:
1.  **Cross-modal rasterizer:** Ablates different modality fusion methods (Table 4.A, Table 11) and the use of the smoothed semantic indicator compared to alternatives like using color opacity or fixed values (Table 4.B, Table 12).
2.  **Camera-view blending:** Ablates the components of the blending technique (Rotation, Translation, SSIM weighting) (Table 5, Table 14) and the sampling distribution for the interpolation ratio `k` (Table 4.C, Table 15, Table 16). It also compares the proposed online view blending to an offline data augmentation strategy (Table 13).
3.  **Disentanglement Level:** Ablates different levels of sharing/disentangling Gaussian parameters between modalities (Table 17).

While these ablations cover the core proposed mechanisms (rasterizer components, blending components), they do not fully explore the impact of the *inputs* to the system or the *overall loss function balance*.

Based on this analysis, two important missing ablation studies are:

1.  **Source of Ground Truth Semantic Features:** The method relies heavily on the quality and nature of the 2D language features extracted from input images using off-the-shelf models (SAM+CLIP in this paper). An ablation studying the impact of using different feature extractors (e.g., CLIP alone, LSeg, APE, DINOv2) would reveal how dependent the method's performance is on the specific choice of the upstream vision-language model or feature source. This is crucial for understanding the generalizability and limitations of the approach. The paper mentions other VLMs in related work but doesn't test them as input sources.
2.  **Weight of Camera View Blending Loss:** The overall loss function (Eq. 12) combines the rasterization loss and the camera view blending loss with a trade-off parameter λ, fixed at 1.2 in the experiments. While the paper shows that including view blending (λ=1.2) is better than not including it (implicitly λ=0 in Table 9/10), it does not explore the sensitivity of the performance to the specific value of λ. Ablating λ across a range of values would demonstrate the importance of the regularization term relative to the main fitting objective and provide insight into hyperparameter tuning.

These two ablations are important because they investigate the influence of the input data characteristics and the balance of the training objective, respectively, which are fundamental aspects of the proposed method not fully explored in the current ablation section. I rank the source of input features as slightly more important as it dictates the very nature of the semantic information the model learns from.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on GT Semantic Feature Source
- **Ablated Part**: Method used to extract ground-truth 2D language features (currently SAM+CLIP)
- **Action**: REPLACE
- **Replacement**: 
  - CLIP features only
  - LSeg features
- **Metrics**: mIoU (LERF avg.), Localization Accuracy (LERF avg.), mIoU (3D-OVS avg.)

### Ablation on Blending Loss Weight
- **Ablated Part**: Hyper-parameter lambda controlling the weight of the camera view blending loss
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.5
  - 1.0
  - 2.0
- **Metrics**: mIoU (LERF avg.), Localization Accuracy (LERF avg.), mIoU (3D-OVS avg.)

</div>