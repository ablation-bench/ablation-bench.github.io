<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/gpt-gnn

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

In our proposed ablation plan, we target the core components that contribute to the performance of GPT‐GNN. First, we evaluate the importance of the dependency‐aware factorization that couples attribute generation and edge generation by completely removing the coupling to see how much the interaction contributes to capturing structure–attribute dependencies. Second, we investigate the design choice of separating node representations into two types (Attribute Generation vs. Edge Generation) by replacing it with a unified representation to understand if avoiding information leakage is essential. Third, we examine the effect of the adaptive negative sampling queue in the edge generation task by removing it, which assesses how global negative samples improve the contrastive loss. Fourth, we study the sensitivity of the observed versus masked edge ratio used in the factorized generation process by experimenting with different ratios. Finally, we explore how subgraph sampling strategies for large-scale graphs affect performance by replacing the LADIES/HGSampling method with alternatives like uniform sampling. We report downstream metrics such as node classification accuracy and link prediction AUC (as reported in the paper) as well as intrinsic generation losses (e.g., attribute generation perplexity and edge contrastive loss) when applicable.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Coupling Ablation
- **Ablated Part**: Dependency-aware factorization that jointly models attribute and edge generation to capture their inherent dependency.
- **Action**: REMOVE
- **Metrics**: node classification accuracy, link prediction AUC, attribute generation perplexity

### Unified Node Representation Ablation
- **Ablated Part**: Separation of nodes into Attribute Generation and Edge Generation types to avoid information leakage.
- **Action**: REPLACE
- **Replacement**: 
  - Unified node representation (single input for both tasks)
- **Metrics**: node classification accuracy, link prediction AUC

### Without Adaptive Negative Queue Ablation
- **Ablated Part**: Adaptive node embedding queue that provides cross subgraph negative samples for edge contrastive learning.
- **Action**: REMOVE
- **Metrics**: node classification accuracy, link prediction AUC, edge generation contrastive loss

### Edge Masking Ratio Sensitivity Ablation
- **Ablated Part**: Fixed ratio of observed edges versus masked edges used during the factorized generation process.
- **Action**: REPLACE
- **Replacement**: 
  - 0.2 observed ratio
  - 0.5 observed ratio
  - 0.8 observed ratio
- **Metrics**: node classification accuracy, link prediction AUC, attribute generation perplexity

### Subgraph Sampling Strategy Ablation
- **Ablated Part**: Subgraph sampling method used to pre-train on large-scale graphs (e.g., LADIES/HGSampling) versus alternative methods.
- **Action**: REPLACE
- **Replacement**: 
  - LADIES
  - Uniform Sampling
  - HGSampling
- **Metrics**: node classification accuracy, link prediction AUC

</div>