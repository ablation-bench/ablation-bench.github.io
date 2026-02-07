<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/From_Sparse_to_Dense__Learning_to_Construct_3D_Human_Meshes_from_WiFi

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that while the authors conducted ablation studies on several components (refine decoder, joint differentiation, and phase sanitization), there are still some critical components that weren't tested in ablation studies:

1. CSI Feature Extractor and Encoder Architecture:
The paper uses two independent MLPs to extract features from amplitude and phase, followed by a feature mixer. This is a crucial architectural choice that deserves investigation, as it's the foundation for processing the WiFi signals.

2. Number of Transformer Layers:
The paper mentions using 6 layers in the CSI Feature Encoder, but there's no ablation study showing why this number was chosen and how it affects performance. This is particularly important since the transformer architecture is central to the method.

Given these observations, I'll suggest two critical missing ablation studies, ranked by importance:
1. Testing the CSI feature extraction architecture, as this is fundamental to the method's ability to process WiFi signals
2. Investigating the impact of encoder layers, as this affects both performance and computational efficiency
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### CSI Feature Architecture Ablation
- **Ablated Part**: CSI feature extraction architecture (separate MLPs for amplitude and phase)
- **Action**: REPLACE
- **Replacement**: 
  - single MLP for combined amplitude-phase
  - three separate MLPs (amplitude, phase, cross-features)
- **Metrics**: MPJPE, PAMPJPE, PVE

### Encoder Depth Ablation
- **Ablated Part**: number of transformer layers in CSI Feature Encoder
- **Action**: REPLACE
- **Replacement**: 
  - 2 layers
  - 4 layers
  - 8 layers
  - 10 layers
- **Metrics**: MPJPE, PAMPJPE, PVE

</div>