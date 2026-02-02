<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/rah-kbqa

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, the main novel components of the method are:

1. The dual relation graph construction and propagation - this is a key innovation where relations that share head/tail entities are connected.

2. The iterative interaction between primal entity graph and dual relation graph - the method uses both graphs to enhance representations.

3. The entity-aware relation updating using TransE assumptions - incorporating head-tail entity information to enhance relation representations.

4. The relation-aware entity updating using separate projectors for head/tail entities.

The most important ablations should test:

1. The value of the dual relation graph by removing it completely
2. The importance of the iterative interaction between graphs
3. The effectiveness of the TransE-based entity-aware relation updating
4. The benefit of using separate projectors for head/tail entities
5. The number of interaction iterations

The metrics used in the paper are Hits@1 and F1 score on WebQSP and CWQ datasets.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Dual Graph
- **Ablated Part**: Dual relation graph and its propagation mechanism
- **Action**: REMOVE
- **Metrics**: Hits@1, F1

### No Graph Interaction
- **Ablated Part**: Iterative interaction between primal and dual graphs
- **Action**: REMOVE
- **Metrics**: Hits@1, F1

### No TransE Integration
- **Ablated Part**: Entity-aware relation updating using TransE assumptions
- **Action**: REMOVE
- **Metrics**: Hits@1, F1

### Unified Head-Tail Projector
- **Ablated Part**: Separate projectors for head/tail entities
- **Action**: REPLACE
- **Replacement**: 
  - Single unified projector
- **Metrics**: Hits@1, F1

### Interaction Iterations
- **Ablated Part**: Number of interaction iterations between graphs
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 2
  - 3
  - 4
  - 5
- **Metrics**: Hits@1, F1

</div>