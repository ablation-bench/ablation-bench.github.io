<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Resolving_Lexical_Bias_in_Edit_Scoping_with_Projector_Editor_Networks

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The first proposed ablation study we suggest is to remove the added contrastive loss constraint that enforces greater inter-edit separation. Although the paper highlights that this additional term is critical for mitigating misclassifications due to the inherent lexical similarities among edits, the impact of this constraint is not isolated in the ablation studies. Removing this component can help determine its contribution to overall performance in terms of Edit Success (ES), Locality (Loc), Paraphrase Generalization (Para), and the overall Score.

The second ablation study focuses on the architecture of the projection network. PENME uses a compact two-layer feedforward network; however, the sensitivity of the editing performance to the network’s depth is not explored. By replacing the two-layer structure with alternatives such as a simpler one-layer network or a deeper three-layer network, we can assess whether the chosen architectural design is optimal. This study would measure the same performance metrics, providing insight on trade-offs between network complexity and editing efficiency.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A: Remove Additional Contrastive Constraint
- **Ablated Part**: The extra loss component in the contrastive loss that enforces maximized inter-edit distances
- **Action**: REMOVE
- **Metrics**: ES, Loc, Para, Score

### Ablation B: Projection Network Depth Variation
- **Ablated Part**: The two-layer architecture of the projection network
- **Action**: REPLACE
- **Replacement**: 
  - 1-layer
  - 3-layer
- **Metrics**: ES, Loc, Para, Score

</div>