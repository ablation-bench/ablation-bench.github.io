<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Multi_Vector_Retrieval_as_Sparse_Alignment

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

From analyzing the paper, I notice that the authors have already conducted several ablation studies, including:
1. Testing different pairwise alignment strategies (top-k and top-p)
2. Testing different model sizes (base, large, xl, xxl)
3. Testing different sparsity ratios for unary salience
4. Testing different entropy regularization parameters for the linear programming

However, I identify two critical missing ablation studies:

1. The choice of similarity function between query and document tokens. The paper uses dot product (q_i^T d_j) but doesn't investigate other similarity metrics that could potentially improve alignment quality.

2. The impact of the token representation dimensionality. The paper mentions projecting token embeddings to 128 dimensions but doesn't justify this choice or explore its impact on performance vs efficiency tradeoff.

These ablations are important because:
- The similarity function is fundamental to the alignment mechanism
- The embedding dimension directly affects both model performance and computational/storage costs
- Both components are major design choices that could significantly impact the method's effectiveness

The metrics used should match those in the paper: MRR@10 for MS MARCO and nDCG@10 for BEIR benchmark.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Similarity Function Ablation
- **Ablated Part**: Token similarity function (currently dot product)
- **Action**: REPLACE
- **Replacement**: 
  - cosine similarity
  - scaled dot product
  - L2 distance
- **Metrics**: MRR@10, nDCG@10

### Token Dimension Ablation
- **Ablated Part**: Token embedding projection dimension (currently 128)
- **Action**: REPLACE
- **Replacement**: 
  - 64
  - 256
  - 512
- **Metrics**: MRR@10, nDCG@10

</div>