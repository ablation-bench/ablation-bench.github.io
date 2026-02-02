<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Spatial_Attention_Kinetic_Networks_with_E_n__Equivariance

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Spatial Attention Kinetic Networks with E(n)-Equivariance" introduces SAKE, a novel E(n)-equivariant graph neural network architecture. The core novelty is the "spatial attention" functional form (Eq. 6), which uses neurally parametrized linear combinations of edge vectors. The architecture also includes specific designs for edge embedding (Eq. 7), semantic attention (Eq. 10), and a fictitious velocity integration mechanism (Eq. 12, 13).

The paper includes an ablation study in Section 6.3 (Table 7) on the MD17-Aspirin dataset. This study ablates the presence of three components:
1.  Spatial attention (Eq. 6)
2.  Semantic attention (Eq. 10)
3.  Velocity and position update (Eq. 12)

The results show that spatial attention consistently improves performance, and the other two components also contribute positively.

Based on the method description and the existing ablations, I identify two important components/design choices that were not ablated:

1.  **The specific form of the Edge Embedding (Eq. 7):** The paper uses a relatively complex edge embedding that combines concatenation of node embeddings and distance, RBF expansion of distance, and a filter network applied to node embeddings. This is a crucial step as it generates the features that are then used by the spatial attention and other parts of the network. Ablating different aspects of this edge embedding (e.g., removing RBF, removing the filter network, or using a simpler embedding) would reveal the contribution of this specific design to SAKE's performance. This is a fundamental part of the message-passing process.
2.  **The number of Spatial Attention Heads (Nλ):** The spatial attention mechanism (Eq. 6) is described as analogous to multi-head attention, using Nλ sets of attention weights. The paper uses 4 heads in its experiments (mentioned in Section 9.3). Ablating the number of heads (e.g., comparing 1, 2, 4, 8 heads) would demonstrate the impact of this multi-head design within the novel spatial attention mechanism. This directly investigates a hyperparameter choice within the core novel component.

Both of these ablations are important for understanding which specific design choices contribute most to SAKE's performance and efficiency. Ablating the edge embedding seems slightly more fundamental as it affects the input features for subsequent steps, including spatial attention. Therefore, I prioritize it first.

The metrics used in the existing ablation study (Table 7) are Energy RMSE and Force RMSE on MD17-Aspirin. The paper also reports MAE for these tasks (Table 1) and inference time. For consistency and comprehensive evaluation, I will suggest reporting Energy MAE, Force MAE, Energy RMSE, Force RMSE, and Inference time for these missing ablations, focusing on the MD17-Aspirin task as in the original ablation study.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablate Edge Embedding Complexity
- **Ablated Part**: The specific edge embedding function combining distance, RBF, and filter network (Eq. 7)
- **Action**: REPLACE
- **Replacement**: 
  - Distance only
  - Distance + MLP
  - Distance + RBF (no filter network)
- **Metrics**: Energy MAE (meV), Force MAE (meV/Å), Energy RMSE (meV), Force RMSE (meV/Å), Inference time (ms)

### Ablate Spatial Attention Heads
- **Ablated Part**: The number of attention heads (Nλ) in the spatial attention mechanism (Eq. 6)
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 2
  - 8
- **Metrics**: Energy MAE (meV), Force MAE (meV/Å), Energy RMSE (meV), Force RMSE (meV/Å), Inference time (ms)

</div>