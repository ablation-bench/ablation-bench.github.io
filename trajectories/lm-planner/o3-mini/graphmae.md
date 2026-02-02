<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/graphmae

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The key components that uniquely empower GraphMAE are the careful use of (1) a scaled cosine error loss, (2) a feature-masking strategy to force denoising and prevent trivial identity learning, (3) a re-mask decoding step that further challenges the reconstruction, (4) the use of an expressive GNN in the decoder versus a traditional MLP, and (5) the design choice of focusing purely on feature reconstruction instead of including structure reconstruction. To thoroughly assess the contribution of each design, we propose ablation studies that (i) replace or remove the scaled cosine error loss to compare with standard losses (such as MSE and plain cosine error), (ii) remove the mask corruption to gauge its effect on preventing trivial solutions, (iii) remove the re-mask decoding step to test its benefit in enforcing cross-node information exchange, (iv) replace the GNN decoder with a simpler MLP decoder, and (v) replace the pure feature reconstruction objective with a joint feature and structure reconstruction objective. These studies will be evaluated on downstream performance metrics such as node classification accuracy, graph classification accuracy, and the reconstruction error.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Reconstruction Loss Variation
- **Ablated Part**: Scaled cosine error loss used for feature reconstruction
- **Action**: REPLACE
- **Replacement**: 
  - MSE
  - Cosine Error
  - Scaled Cosine Error with gamma=1
  - Scaled Cosine Error with gamma=2
  - Scaled Cosine Error with gamma=3
- **Metrics**: Reconstruction Error, Node Classification Accuracy, Graph Classification Accuracy

### Ablation: Masking Strategy
- **Ablated Part**: Input feature masking with [MASK] token
- **Action**: REMOVE
- **Metrics**: Reconstruction Error, Node Classification Accuracy, Graph Classification Accuracy

### Ablation: Re-mask Decoding
- **Ablated Part**: Re-masking of encoded latent representations before decoding
- **Action**: REMOVE
- **Metrics**: Reconstruction Error, Node Classification Accuracy, Graph Classification Accuracy

### Ablation: Decoder Architecture
- **Ablated Part**: GNN-based decoder used for reconstructing node features
- **Action**: REPLACE
- **Replacement**: 
  - Simple MLP
  - Linear decoder
- **Metrics**: Reconstruction Error, Node Classification Accuracy, Graph Classification Accuracy

### Ablation: Reconstruction Objective
- **Ablated Part**: Target of reconstruction: feature-only versus joint feature and structure
- **Action**: REPLACE
- **Replacement**: 
  - Feature-only
  - Feature+Structure
- **Metrics**: Node Classification Accuracy, Graph Classification Accuracy, Link Prediction AUC

</div>