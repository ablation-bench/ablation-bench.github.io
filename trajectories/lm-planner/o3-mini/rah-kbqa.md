<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/rah-kbqa

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose four ablation studies that aim to quantify the contributions of the main novel components in the paper. The first ablation removes the dual relation graph propagation module entirely, thereby testing the model’s reliance on explicit relation‐to‐relation communications produced using GAT. The second study removes the entity-aware relation updating mechanism which integrates head–tail entity difference (following a TransE assumption) into relation representations. This helps us understand how much the head–tail information contributes when building better relation embeddings. The third experiment replaces the GAT aggregator used in the dual graph propagation with simpler alternatives (e.g., Mean or GCN aggregators) to assess whether the attention mechanism in GAT is critical or if a more straightforward aggregation can suffice. Finally, the fourth ablation disables the iterative instruction adaption mechanism in the question encoder, which updates question instructions based on entity representations during reasoning. By holding instructions fixed, we can evaluate how much the dynamic grounding of instructions contributes to the model’s overall performance. All studies will be evaluated using the same metrics as the paper (Hits@1 and F1 scores) to ensure comparability.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Dual Graph Removal
- **Ablated Part**: Dual Relation Graph Propagation module that uses GAT to propagate semantic information between relations
- **Action**: REMOVE
- **Metrics**: Hits@1, F1

### Ablation Head-Tail Integration Removal
- **Ablated Part**: Entity-Aware Relation Updating component that integrates head-tail entity differences (TransE assumption) into relation representations
- **Action**: REMOVE
- **Metrics**: Hits@1, F1

### Ablation Aggregator Replacement
- **Ablated Part**: GAT aggregator in the Dual Relation Graph Propagation module
- **Action**: REPLACE
- **Replacement**: 
  - Mean Aggregator
  - GCN Aggregator
- **Metrics**: Hits@1, F1

### Ablation Iterative Instruction Adaption Removal
- **Ablated Part**: Iterative Instruction Adaption mechanism in the question encoder that updates instructions based on entity representations
- **Action**: REMOVE
- **Metrics**: Hits@1, F1

</div>