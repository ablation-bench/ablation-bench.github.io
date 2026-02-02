<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/unsup3d

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants a list of up to 5 ablation studies for the paper "Unsupervised Learning of Probably Symmetric Deformable 3D Objects from Images in the Wild". I need to identify the key components of the method and propose ablations, ranking them by importance.

The core of the method is an unsupervised autoencoder that disentangles depth, albedo, viewpoint, and illumination by leveraging the assumption of bilateral symmetry. Key mechanisms include:
1.  Using a flipped reconstruction based on flipped depth and albedo to enforce symmetry implicitly.
2.  Modeling asymmetric illumination by separating albedo and shading.
3.  Predicting a symmetry probability map ($\sigma'$) to handle non-symmetric parts via a separate confidence-weighted loss for the flipped reconstruction.
4.  Using learned confidence maps ($\sigma, \sigma'$) for the reconstruction losses (both standard and flipped).
5.  Including a perceptual loss term.

Based on these components and the paper's emphasis, I will propose the following ablations, ranked by their perceived importance in validating the core contributions:

1.  **Remove Symmetry Constraint:** This is the most fundamental assumption. Removing the flipped reconstruction loss tests whether the symmetry principle is necessary for unsupervised 3D learning in this framework.
2.  **Fixed Asymmetric Confidence:** The learned symmetry probability map ($\sigma'$) is a novel way to handle real-world asymmetries. Replacing the learned $\sigma'$ with a fixed value tests the importance of the *learned, pixel-wise* confidence for the symmetric view.
3.  **Combined Albedo and Illumination:** The paper argues that separating albedo and illumination is beneficial for exploiting symmetry and shading cues. Ablating this tests this specific design choice.
4.  **Remove Perceptual Loss:** The perceptual loss is a common technique but its impact on the geometric disentanglement and accuracy in this unsupervised 3D context is worth evaluating.
5.  **Fixed Reconstruction Confidence:** The paper uses learned confidence maps ($\sigma, \sigma'$) for both reconstruction losses. Replacing these with fixed values tests the overall benefit of learned uncertainty calibration. The paper's Table 3 already provides some comparison related to this ("conf" vs "no conf"), but a formal ablation entry is still relevant.

The metrics used in the paper's ablation studies (Table 3) are SIDE ($\downarrow$) and MAD (deg.) ($\downarrow$). These are appropriate metrics for evaluating the geometric accuracy of the reconstructions on the BFM dataset, which the paper uses for controlled ablations. I will use these metrics for the proposed ablations.

I will format the output as a JSONL list within the `predictions` field, following the specified structure.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Symmetry Constraint
- **Ablated Part**: Flipped reconstruction loss based on symmetry
- **Action**: REMOVE
- **Metrics**: SIDE, MAD

### Fixed Asymmetric Confidence
- **Ablated Part**: Learned confidence map for flipped reconstruction (sigma')
- **Action**: REPLACE
- **Replacement**: 
  - 1.0
- **Metrics**: SIDE, MAD

### Combined Albedo and Illumination
- **Ablated Part**: Separation of albedo and illumination
- **Action**: REPLACE
- **Replacement**: 
  - Combined texture map
- **Metrics**: SIDE, MAD

### No Perceptual Loss
- **Ablated Part**: Perceptual loss term
- **Action**: REMOVE
- **Metrics**: SIDE, MAD

### Fixed Reconstruction Confidence
- **Ablated Part**: Learned confidence maps for reconstruction (sigma, sigma')
- **Action**: REPLACE
- **Replacement**: 
  - 1.0
- **Metrics**: SIDE, MAD

</div>