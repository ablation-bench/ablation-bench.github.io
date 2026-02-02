<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/gpt-gnn

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, GPT-GNN's main contributions are:
1. A novel attributed graph generation task that factorizes into Attribute Generation and Edge Generation
2. An efficient framework to conduct generative pre-training
3. Handling of large-scale graphs using sub-graph sampling and adaptive embedding queue

Key ablation studies should focus on:
1. The importance of the dual-generation approach (attributes and edges)
2. The effectiveness of the adaptive queue for negative samples
3. The impact of separating nodes into Attribute Generation and Edge Generation types
4. The sampling strategy for observed vs. masked edges
5. The sub-graph sampling approach for large graphs

I'll rank these by importance and formulate specific ablation experiments:
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Dual Generation Ablation
- **Ablated Part**: The dual generation approach (attribute and edge generation)
- **Action**: REPLACE
- **Replacement**: 
  - edge generation only
  - attribute generation only
- **Metrics**: node classification accuracy, link prediction AUC, perplexity

### Adaptive Queue Ablation
- **Ablated Part**: Adaptive embedding queue for negative samples
- **Action**: REPLACE
- **Replacement**: 
  - random negative sampling
  - no queue (only use current batch)
- **Metrics**: link prediction AUC, edge generation loss

### Node Separation Ablation
- **Ablated Part**: Separation of nodes into Attribute Generation and Edge Generation types
- **Action**: REMOVE
- **Metrics**: attribute generation loss, edge generation loss, node classification accuracy

### Edge Observation Ablation
- **Ablated Part**: Edge masking strategy
- **Action**: REPLACE
- **Replacement**: 
  - random edge masking
  - uniform masking ratio
  - structural role-based masking
- **Metrics**: edge generation loss, link prediction AUC

### Subgraph Sampling Ablation
- **Ablated Part**: LADIES algorithm for subgraph sampling
- **Action**: REPLACE
- **Replacement**: 
  - random node sampling
  - random walk sampling
  - neighborhood sampling
- **Metrics**: node classification accuracy, training efficiency, memory usage

</div>