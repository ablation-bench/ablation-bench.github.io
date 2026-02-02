<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/REBIND__Enhancing_Ground_state_Molecular_Conformation_Prediction_via_Force_Based_Graph_Rewiring

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "REBIND: Enhancing Ground-state Molecular Conformation Prediction via Force-Based Graph Rewiring" proposes a novel framework that addresses the limitations of existing deep learning methods in modeling non-bonded inter-atomic forces, particularly for low-degree atoms. The core idea is to rewire the molecular graph by adding edges based on Lennard-Jones potential forces calculated from an initial conformation prediction. The edge augmentation is performed in a degree-compensating manner, prioritizing low-degree atoms. These force-based edges (distinguishing attractive and repulsive forces) are then incorporated as residuals in the multi-head self-attention mechanism of a decoder, which refines the initial conformation.

The paper includes several ablation studies in Section 5.4 and Appendix B.6. These ablations demonstrate:
1.  The benefit of incorporating bonded edges (Abond) compared to a vanilla transformer (Table 3).
2.  The superiority of force-aware edges (Aforce) over distance-based edges (Anear) for non-bonded interactions (Table 3).
3.  The overall contribution of Abond and Aforce components (Table 3).
4.  The generalizability of the REBIND concept (encoder-decoder with force rewiring) to different GNN backbones (Table 4).
5.  Exploration of various combinations of adjacency matrices (Abond, Drow-sub, Aforce, Anear) as residuals (Table 8).

While these ablations cover important aspects, two key components of the proposed rewiring mechanism are not thoroughly investigated:

1.  **The Degree-Compensating Rewiring Strategy:** The paper emphasizes that the rewiring is degree-compensating to specifically help low-degree atoms, which are identified as a weakness in prior methods (Section 3). The mechanism adds `max_deg - deg_i` edges to atom `i`. However, the ablation studies do not directly compare this specific degree-dependent strategy against alternative, simpler strategies for selecting the number of force-based edges, such as adding a fixed number of top-force edges to every atom regardless of its degree. Ablating this would quantify the specific benefit of the degree-compensation.

2.  **The Source of Distances for Force Calculation:** REBIND calculates LJ forces using distances derived from the *predicted* initial conformation from the encoder (D_enc). This means the quality of the force-based edges depends on the accuracy of the encoder's prediction. An important ablation would be to evaluate the potential performance gain if the force calculation during training used the *ground-truth* distances (D). This would isolate the effectiveness of the force-aware rewiring mechanism itself, independent of the encoder's initial prediction quality, providing an upper bound on its potential and highlighting the impact of using predicted distances.

Therefore, I propose two missing ablation studies focusing on these aspects. The metrics should include both molecule-level metrics (D-MAE, D-RMSE, C-RMSD, E-RMSD) and atom-wise metrics (RMSD, MAE, E-RMSD) broken down by low/high degree, as these are used throughout the paper to support the claims about low-degree atoms.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Rewiring Strategy
- **Ablated Part**: Degree-compensating strategy for adding force-based edges.
- **Action**: REPLACE
- **Replacement**: 
  - Fixed number of top-force edges per atom (K=1)
  - Fixed number of top-force edges per atom (K=3)
  - Fixed number of top-force edges per atom (K=5)
- **Metrics**: D-MAE, D-RMSE, C-RMSD, E-RMSD, Atom-wise RMSD (low/high degree), Atom-wise MAE (low/high degree), Atom-wise E-RMSD (low/high degree)

### Ablation: Force Distance Source (Training)
- **Ablated Part**: Using predicted encoder distances (D_enc) for LJ force calculation during training.
- **Action**: REPLACE
- **Replacement**: 
  - Ground-truth distances (D) for LJ force calculation during training
- **Metrics**: D-MAE, D-RMSE, C-RMSD, E-RMSD, Atom-wise RMSD (low/high degree), Atom-wise MAE (low/high degree), Atom-wise E-RMSD (low/high degree)

</div>