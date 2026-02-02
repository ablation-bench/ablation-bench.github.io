<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/unsup3d

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents a method for unsupervised learning of 3D deformable objects from single-view images by leveraging symmetry and illumination. The method decomposes images into depth, albedo, viewpoint, and illumination using an autoencoder. Key components include the symmetry probability map and the confidence maps for handling asymmetries. The ablation studies should focus on these components to understand their contributions to the model's performance.

1. Symmetry Probability Map: This component is crucial for handling objects that are not perfectly symmetric. Ablating this part will help understand its impact on the model's ability to reconstruct 3D shapes accurately.

2. Confidence Maps: These maps are used to model uncertainty and handle asymmetries in the input images. Removing or altering these maps can reveal their importance in the reconstruction process.

3. Illumination Modeling: The paper emphasizes the role of illumination in exploiting symmetry. An ablation study could involve removing or modifying the illumination component to assess its effect on the model's performance.

4. Perceptual Loss: The perceptual loss is added to improve reconstruction quality. Ablating this loss can help determine its impact on the visual fidelity of the reconstructed images.

5. Symmetry Enforcement: The method enforces symmetry by flipping internal representations. An ablation study could involve removing this enforcement to see how it affects the model's ability to learn symmetric structures.

The metrics to report should include Depth Correlation, SIDE (Scale-Invariant Depth Error), and MAD (Mean Angular Deviation), as these are used in the paper to evaluate the model's performance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Symmetry Probability Map
- **Ablated Part**: Symmetry probability map
- **Action**: REMOVE
- **Metrics**: Depth Correlation, SIDE, MAD

### Ablation of Confidence Maps
- **Ablated Part**: Confidence maps for uncertainty modeling
- **Action**: REMOVE
- **Metrics**: Depth Correlation, SIDE, MAD

### Ablation of Illumination Modeling
- **Ablated Part**: Illumination component
- **Action**: REMOVE
- **Metrics**: Depth Correlation, SIDE, MAD

### Ablation of Perceptual Loss
- **Ablated Part**: Perceptual loss
- **Action**: REMOVE
- **Metrics**: Depth Correlation, SIDE, MAD

### Ablation of Symmetry Enforcement
- **Ablated Part**: Symmetry enforcement by flipping internal representations
- **Action**: REMOVE
- **Metrics**: Depth Correlation, SIDE, MAD

</div>