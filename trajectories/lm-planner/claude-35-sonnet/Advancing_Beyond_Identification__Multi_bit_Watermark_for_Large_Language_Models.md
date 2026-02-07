<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Advancing_Beyond_Identification__Multi_bit_Watermark_for_Large_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes MPAC (Multi-bit watermark via Position Allocation), which extends zero-bit watermarking to embed traceable multi-bit information. The key components are:

1. Position allocation: Assigns each token to a message position using a hashing scheme
2. Colorlisting: Partitions vocabulary into r "colored" lists to encode multiple states per token
3. Bias magnitude (δ): Controls the strength of favoring tokens from the selected colorlist

The paper already includes ablations on:
- Different hash schemes (LeftHash vs SelfHash)
- Different colorlist proportions (γ) and radix (r) values
- Different bias magnitudes (δ)
- Different model sizes and datasets

However, I notice two important missing ablations:

1. The position allocation strategy is crucial but only pseudo-random allocation is thoroughly tested. While they briefly mention rule-based schemes like sequential allocation, a proper ablation comparing different allocation strategies would be valuable.

2. The paper uses a fixed bias magnitude δ across all positions and colorlists. An ablation studying position-specific or colorlist-specific bias values could reveal if adaptive biasing improves performance.

These ablations would help better understand the key design choices of MPAC.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Position Allocation Strategy Ablation
- **Ablated Part**: Position allocation method
- **Action**: REPLACE
- **Replacement**: 
  - sequential
  - cyclic
  - pseudo-random
  - deterministic
- **Metrics**: bit accuracy, AUC, perplexity, P-SP

### Adaptive Bias Ablation
- **Ablated Part**: Fixed bias magnitude
- **Action**: REPLACE
- **Replacement**: 
  - position-specific bias
  - colorlist-specific bias
  - adaptive bias based on message content
- **Metrics**: bit accuracy, AUC, perplexity, P-SP

</div>