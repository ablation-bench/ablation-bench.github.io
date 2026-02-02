<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/From_Sparse_to_Dense__Learning_to_Construct_3D_Human_Meshes_from_WiFi

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Our analysis of the paper "From Sparse to Dense: Learning to Construct 3D Human Meshes from WiFi" shows that several key design choices are rigorously ablated (for example, the refine decoder, the differentiation branch for joint queries, and the phase sanitization process). However, two important aspects of the overall pipeline have not been directly evaluated. First, the use of an identity token within the refine decoder is proposed to help distinguish among multiple individuals in a scene. Although the paper studies the effect of differentiating joint queries, it does not measure the impact of completely removing the identity token. Evaluating this would clarify how much person-specific information the identity token contributes to the final mesh accuracy. Second, in Section 3.1 the authors introduce a novel tokenization strategy where the CSI signal is flattened to form a token sequence. Previous works have used CNN-based methods (which explicitly preserve the spatial structure of the CSI input). An ablation comparing the current flattening method with a CNN-based token extraction would provide insight into whether the novel tokenization choice is indeed optimal. These missing ablations are ranked in order of importance, with the identity token ablation being the top candidate because of its central role in multi-person differentiation.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Identity Token Ablation
- **Ablated Part**: Identity token in the refine decoder responsible for encoding person-specific information
- **Action**: REMOVE
- **Metrics**: MPJPE, PAMPJPE, PVE

### Tokenization Strategy Ablation
- **Ablated Part**: Method for tokenizing the CSI signals into feature tokens
- **Action**: REPLACE
- **Replacement**: 
  - Flattening approach (current)
  - CNN-based token extraction preserving spatial and temporal structure
- **Metrics**: MPJPE, PAMPJPE, PVE

</div>