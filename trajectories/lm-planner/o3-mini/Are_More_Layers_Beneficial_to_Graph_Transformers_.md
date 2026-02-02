<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Are_More_Layers_Beneficial_to_Graph_Transformers_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper already presents ablation studies on local attention, substructure encoding (by comparing with a random initialization baseline), deepnorm, sensitivity to substructure types, and even analyzes neighbor size. However, two important aspects remain unexplored. First, the sampling process used to select substructures is described in detail but its impact on model performance has not been ablated. Varying the number (or ratio) of sampled substructures relative to the overall graph size could affect both the coverage of critical substructures and the resulting attention capacity. Second, the method introduces a permutation-based DFS pooling for substructure token encoding, which is a core design choice. Replacing this complex encoding with simpler aggregation methods (e.g., average, max, or sum pooling) would help determine how critical the DFS-based strategy is for achieving the enhanced attention capacity in deep layers. Testing these two aspects would provide further insights on the sensitivity and necessity of these design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Substructure Sampling Ratio
- **Ablated Part**: Substructure sampling strategy (number of substructures sampled relative to graph size)
- **Action**: REPLACE
- **Replacement**: 
  - Low sampling (e.g., 0.25×|Nodes|)
  - Medium sampling (e.g., 0.5×|Nodes|)
  - High sampling (e.g., |Nodes|)
- **Metrics**: Graph regression MSE (e.g., on ZINC, PCQM4M-LSC), Node classification accuracy (e.g., on CLUSTER, PATTERN), Attention capacity metrics

### Ablation: Substructure Token Encoding Strategy
- **Ablated Part**: Substructure token encoder (DFS-based permutation pooling)
- **Action**: REPLACE
- **Replacement**: 
  - Average pooling
  - Max pooling
  - Sum pooling
- **Metrics**: Graph regression MSE, Node classification accuracy, Substructure representation capacity (max difference among substructure tokens)

</div>