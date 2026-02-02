<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/cet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies to better understand the contributions of each component in CET. First, by completely removing the causal objective (i.e. the colliding effects that preserve pre-trained knowledge), we can measure the overall benefit of incorporating causal inference compared to vanilla fine-tuning. Second, we investigate the sensitivity of the preservation strength by varying the hyperparameter W₀, which controls the weighting between the anchor sample and its KNNs in the causal effect estimation. Third, we assess the impact of the selective application of colliding effects by comparing the default threshold‐based (selective) mechanism to a uniform application on all samples. Fourth, since the KNN retrieval is central to estimating colliding effects, we test alternative similarity metrics (e.g. cosine similarity on hidden states, textual overlap) against the heuristic gold answer matching employed in the paper. Finally, we vary the number of nearest neighbors (K) used in the causal effect estimation to gauge how much contextual information is optimal. Together, these ablations will clarify how each design decision contributes to preserving commonsense knowledge in the fine-tuning process.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Remove Causal Objective
- **Ablated Part**: Causal objective (colliding effects) that preserves pre-trained knowledge
- **Action**: REMOVE
- **Metrics**: accuracy

### Vary Preservation Strength (W0)
- **Ablated Part**: Hyperparameter W₀ controlling the balance between anchor sample prediction and KNN contributions in the causal objective
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.3
  - 0.5
  - 0.7
  - 1.0
- **Metrics**: accuracy

### Uniform vs Selective Colliding Effects
- **Ablated Part**: Selective application of colliding effects using a similarity threshold for KNN selection
- **Action**: REPLACE
- **Replacement**: 
  - Force colliding effects on all samples
  - Threshold-based selective preservation
- **Metrics**: accuracy

### Alternative KNN Similarity Metrics
- **Ablated Part**: KNN retrieval mechanism for estimating colliding effects based on similarity metric
- **Action**: REPLACE
- **Replacement**: 
  - Cosine similarity on hidden states
  - Textual overlap
  - Heuristic gold answer matching
- **Metrics**: accuracy

### Vary Number of KNN Neighbors
- **Ablated Part**: Hyperparameter K defining the number of nearest neighbors used in causal effect estimation
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 3
  - 5
  - 7
  - 10
- **Metrics**: accuracy

</div>