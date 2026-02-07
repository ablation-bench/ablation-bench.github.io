<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Using_semantic_distance_for_diverse_and_sample_efficient_genetic_programming

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Looking at the paper's method section, the key components are:
1. The mutation objective function (equation 1) which has three terms:
   - Semantic similarity term (|d(M(G), G) - μ|)
   - Diversity term (-μ tanh(min_H d(M(G), H)/μ))
   - Complexity penalty term (μβv(M(G)))

2. The distance function (equation 2) which uses:
   - Program semantics mapping s(G)
   - Custom scaling p(G)

The paper already includes ablations on the mutation objective terms (Figure 1), showing the importance of diversity and simplicity terms.

However, I notice two important missing ablations:

1. The choice of distance function and semantics mapping is crucial but not ablated. The paper uses L1 distance with different semantics mappings for different applications (identity semantics for regression, gradient semantics for loss functions). Testing alternative distance metrics (e.g., L2) or semantics mappings would help understand their impact.

2. The CMA-ES optimization of constants is a key implementation detail that contributes to the method's efficiency (as mentioned in Section 3.2). The paper doesn't ablate this to quantify its importance compared to simpler constant optimization approaches.

These ablations would help understand which components are truly essential for the method's strong performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Distance Function Ablation
- **Ablated Part**: L1 distance metric in equation 2
- **Action**: REPLACE
- **Replacement**: 
  - L2 distance
  - cosine similarity
  - Jensen-Shannon divergence
- **Metrics**: fitness score, sample efficiency (number of evaluations needed)

### Constants Optimization Ablation
- **Ablated Part**: CMA-ES optimization of constants
- **Action**: REPLACE
- **Replacement**: 
  - random search
  - grid search
  - gradient descent
- **Metrics**: fitness score, wall-clock time, sample efficiency (number of evaluations needed)

</div>