<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/cet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, the main components of the method are:

1. The causal graph framework for fine-tuning that introduces colliding effects between pre-trained data and target data.

2. The K-Nearest Neighbors (KNN) approach to estimate causal effects, where neighbors are selected based on similarity of gold answers.

3. The unified objective that combines vanilla fine-tuning with causal effects preservation.

4. The similarity threshold θ that controls which samples get KNN treatment.

5. The weighting parameter W₀ that balances between anchor sample and its neighbors.

I'll suggest ablation studies focusing on these key components, ranked by importance:

1. First, we should verify the effectiveness of the causal framework by removing it completely.

2. The KNN approach and similarity threshold are critical design choices that should be tested.

3. The weighting scheme between anchor and neighbors is important for balancing knowledge preservation.

4. Alternative similarity metrics for finding neighbors could be explored.

The metrics used in the paper are primarily accuracy on commonsense QA datasets, so we'll use those.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Causal Effects
- **Ablated Part**: Remove the causal effects preservation entirely
- **Action**: REMOVE
- **Metrics**: accuracy

### KNN Selection
- **Ablated Part**: Number of nearest neighbors K
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 3
  - 5
  - 10
- **Metrics**: accuracy

### Similarity Threshold
- **Ablated Part**: Threshold θ for selecting neighbors
- **Action**: REPLACE
- **Replacement**: 
  - 0.5
  - 0.7
  - 0.9
- **Metrics**: accuracy

### Anchor Weight
- **Ablated Part**: Weight W₀ given to anchor sample
- **Action**: REPLACE
- **Replacement**: 
  - 0.3
  - 0.5
  - 0.7
- **Metrics**: accuracy

### Similarity Metric
- **Ablated Part**: Method for computing similarity between samples
- **Action**: REPLACE
- **Replacement**: 
  - cosine similarity of question embeddings
  - exact answer match
  - semantic answer similarity
- **Metrics**: accuracy

</div>