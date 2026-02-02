<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/memorizing-transformers-pytorch

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Below is our prioritized set of ablation studies. The first experiment removes the external memory branch (the kNN-augmented attention component) to quantify its overall contribution compared to only local dense attention. Next, we replace the learned gating mechanism that fuses the kNN and local attention outputs with a fixed interpolation factor (testing several fixed ratios) in order to study the role of gating in balancing short- and long-range signals. Third, we remove the normalization of keys and queries used to mitigate staleness due to distributional shift, to observe its effect on performance. Fourth, we compare the approximate kNN routine with an exact kNN retrieval to evaluate the impact of the approximation on language model perplexity. Finally, while the current design omits any positional bias in the external memory retrieval, we add position bias (using various schemes such as T5 relative or learned absolute biases) to check whether the lack of positional conditioning in the memory branch is beneficial or not. In each case, we report perplexity (as in the paper) which is the primary metric, with the possibility to monitor additional metrics (e.g. retrieval recall or stability) if needed.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Remove kNN Memory Branch
- **Ablated Part**: kNN-augmented attention layer that retrieves external (key, value) pairs
- **Action**: REMOVE
- **Metrics**: perplexity

### Fixed Gate for Memory-Local Attention Combination
- **Ablated Part**: Learned scalar gating mechanism that fuses local dense attention and kNN memory attention
- **Action**: REPLACE
- **Replacement**: 
  - fixed_gate=0.0
  - fixed_gate=0.5
  - fixed_gate=1.0
- **Metrics**: perplexity

### Remove Key/Query Normalization
- **Ablated Part**: Normalization of keys and queries used to alleviate distributional shift in external memory
- **Action**: REMOVE
- **Metrics**: perplexity

### Exact kNN Search versus Approximate kNN
- **Ablated Part**: The approximate kNN search mechanism used in retrieving external memory
- **Action**: REPLACE
- **Replacement**: 
  - exact_kNN
  - approximate_kNN
- **Metrics**: perplexity

### Incorporate Position Bias for External Memory
- **Ablated Part**: Absence of positional bias in the external memory (kNN) retrieval branch
- **Action**: ADD
- **Replacement**: 
  - T5 relative position bias
  - Learned absolute position bias
- **Metrics**: perplexity

</div>