<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/From_Sparse_to_Dense__Learning_to_Construct_3D_Human_Meshes_from_WiFi

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "From Sparse to Dense: Learning to Construct 3D Human Meshes from WiFi" presents a novel approach to reconstructing 3D human meshes from WiFi signals. The authors propose a model called WiMTR, which consists of four key components: CSI feature extractor, CSI feature encoder, coarse decoder, and refine decoder. The model achieves competitive results, with a Mean Per Joint Position Error (MPJPE) of 71.4mm, Procrustes Aligned MPJPE (PAMPJPE) of 29.7mm, and Procrustes Aligned Vertex Error (PVE) of 57.3mm.

The paper includes an ablation study that evaluates the effectiveness of various design choices in the model. However, there are some missing ablation studies that could provide further insights into the model's performance.

One potential missing ablation study is the evaluation of the impact of the number of layers in the CSI feature encoder on the model's performance. The authors use a six-layer encoder, but it would be interesting to see how the model performs with fewer or more layers.

Another potential missing ablation study is the evaluation of the impact of the differentiation branch on the model's performance. The authors introduce a differentiation branch to generate joint queries from the human query, but it would be interesting to see how the model performs without this branch or with alternative designs.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Number of layers in CSI feature encoder
- **Action**: REPLACE
- **Replacement**: 
  - 3
  - 6
  - 9
- **Metrics**: MPJPE, PAMPJPE, PVE

### Ablation Study 2
- **Ablated Part**: Differentiation branch
- **Action**: REMOVE
- **Metrics**: MPJPE, PAMPJPE, PVE

</div>