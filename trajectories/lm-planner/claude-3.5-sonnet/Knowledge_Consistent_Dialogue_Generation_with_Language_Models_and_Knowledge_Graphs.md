<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Knowledge_Consistent_Dialogue_Generation_with_Language_Models_and_Knowledge_Graphs

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes SURGE, a framework for knowledge-consistent dialogue generation with three main components:

1. GNN-based context-relevant subgraph retriever
2. Invariant graph encoding 
3. Graph-text contrastive learning

The paper already includes several ablation studies:
- Varying number of facts in subgraphs (n=3,5,10)
- Different PLM sizes (T5-small vs BART-base)
- GNN variants (GCN vs GAT for retriever, CompGCN vs GCN for encoding)

However, there are two important missing ablations that could help better understand the method's effectiveness:

1. The impact of the graph encoding scheme: The paper proposes a novel invariant and efficient graph encoding method but doesn't fully ablate its components. Testing different variants of the encoding would help understand which properties (permutation invariance, relation inversion invariance) are most important.

2. The effect of contrastive learning parameters: The paper uses contrastive learning with a temperature parameter τ but doesn't study how different temperature values or negative sampling strategies affect performance.

These ablations would provide deeper insights into the key components of the method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Graph Encoding Ablation
- **Ablated Part**: Graph encoding scheme components
- **Action**: REPLACE
- **Replacement**: 
  - naive encoding
  - invariant only
  - efficient only
  - invariant+efficient (full)
- **Metrics**: KQA EM, KQA F1, BLEU, ROUGE, Unigram F1

### Contrastive Learning Ablation
- **Ablated Part**: Contrastive learning parameters
- **Action**: REPLACE
- **Replacement**: 
  - τ=0.001
  - τ=0.01
  - τ=0.1
  - in-batch negatives
  - cross-batch negatives
- **Metrics**: KQA EM, KQA F1, Knowledge F1

</div>