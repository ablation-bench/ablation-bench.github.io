<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/unsup3d

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents an unsupervised method for learning 3D deformable object reconstruction from single-view images. The key novel components that warrant investigation through ablation studies are:

1. Symmetry Modeling: The method heavily relies on symmetry assumptions and uses confidence maps to handle asymmetries. This is a core contribution that should be tested.

2. Illumination Modeling: The paper claims that explicitly modeling illumination helps exploit underlying symmetry even when appearance is asymmetric due to lighting.

3. Perceptual Loss: The method uses both L1 and perceptual losses for reconstruction, with the latter claimed to help avoid blurry results.

4. Pre-training Impact: The paper mentions CelebA pre-training improves results significantly (Table 1).

5. Confidence Maps: The method uses two confidence maps (σ, σ') to handle asymmetries probabilistically.

I'll prioritize testing these components in order of their likely importance to the method's performance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Symmetry Ablation
- **Ablated Part**: symmetry-based reconstruction loss
- **Action**: REMOVE
- **Metrics**: Depth Correlation, SIDE, MAD

### Illumination Model
- **Ablated Part**: explicit illumination modeling
- **Action**: REPLACE
- **Replacement**: 
  - direct texture prediction
  - ambient-only lighting
- **Metrics**: Depth Correlation, SIDE, MAD

### Confidence Maps
- **Ablated Part**: confidence maps σ and σ'
- **Action**: REMOVE
- **Metrics**: Depth Correlation, SIDE, MAD

### Loss Function
- **Ablated Part**: perceptual loss
- **Action**: REPLACE
- **Replacement**: 
  - L1 loss only
  - L2 loss
  - SSIM loss
- **Metrics**: Depth Correlation, SIDE, MAD

### Pre-training
- **Ablated Part**: CelebA pre-training
- **Action**: REMOVE
- **Metrics**: Depth Correlation, SIDE, MAD

</div>