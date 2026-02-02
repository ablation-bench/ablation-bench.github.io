<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Transferring_Pretrained_Diffusion_Probabilistic_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two missing ablation studies that would further clarify the contribution of major components in the proposed condition-based tuning method. First, although the paper inserts the attention-nonlinear (ANL) modules after every residual convolutional block of the U-Net, it does not study how the placement of these modules affects transfer performance. Varying the insertion locations (for example, only in early layers vs. middle/high-level layers) can reveal which levels of representation benefit the most from the semantic guidance. Second, the ANL module uses a cross-attention fusion mechanism followed by a non-linear mapping to inject the CLIP-based semantic embeddings. An ablation that replaces the cross-attention fusion with alternative conditioning strategies (e.g., FiLM, AdaIN, or simple concatenation followed by an MLP) would help validate whether cross-attention is indeed the best design choice for harmonizing the pretrained DPM features with the external condition. Both ablation studies would be evaluated using the same metrics as in the paper (FID, Inception Score, and SSL classification accuracy) to maintain consistency with the original evaluation.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: ANL Module Placement
- **Ablated Part**: Positioning of the ANL module within the U-Net architecture
- **Action**: REPLACE
- **Replacement**: 
  - Insert ANL modules only in early layers
  - Insert ANL modules only in middle layers
  - Insert ANL modules only in high-level layers
  - Insert ANL modules in all layers (baseline)
- **Metrics**: FID, IS, SSL classification accuracy

### Ablation: Fusion Mechanism in ANL Module
- **Ablated Part**: Fusion method for injecting CLIP embeddings into the pretrained DPM
- **Action**: REPLACE
- **Replacement**: 
  - FiLM modulation
  - AdaIN
  - Concatenation+MLP
- **Metrics**: FID, IS, SSL classification accuracy

</div>