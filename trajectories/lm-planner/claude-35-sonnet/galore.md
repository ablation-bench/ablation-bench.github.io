<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/galore

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, GaLore's key innovation is using gradient low-rank projection to enable memory-efficient training while maintaining full-parameter learning capability. The main components that deserve ablation studies are:

1. The rank parameter (r) used for gradient projection - this directly impacts memory efficiency and performance tradeoff.

2. The subspace change frequency (T) - how often the projection matrices P and Q are recomputed using SVD. This is crucial for allowing learning in different subspaces.

3. The scale factor (α) - controls the strength of low-rank updates, similar to LoRA's scale factor.

4. The projection strategy - using one vs two projection matrices (P and Q).

5. The gradient projection approach itself vs other memory reduction techniques.

The key metrics used in the paper are:
- Memory usage (GB)
- Training loss/perplexity 
- Downstream task performance (e.g., GLUE scores for fine-tuning)

I'll prioritize the most important ablations that would help validate the key claims and design choices of the method.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Rank Ablation
- **Ablated Part**: Rank parameter r for gradient projection
- **Action**: REPLACE
- **Replacement**: 
  - 4
  - 8
  - 16
  - 32
  - 64
- **Metrics**: Memory usage (GB), Training loss, GLUE score

### Subspace Change Frequency
- **Ablated Part**: Frequency T of updating projection matrices
- **Action**: REPLACE
- **Replacement**: 
  - 50
  - 200
  - 500
  - 1000
- **Metrics**: Training loss, Memory usage (GB)

### Projection Strategy
- **Ablated Part**: Using one vs two projection matrices
- **Action**: REPLACE
- **Replacement**: 
  - single_projection
  - double_projection
- **Metrics**: Memory usage (GB), Training loss

### Scale Factor
- **Ablated Part**: Scale factor α for gradient updates
- **Action**: REPLACE
- **Replacement**: 
  - 0.1
  - 0.5
  - 1.0
  - 2.0
  - 4.0
- **Metrics**: Training loss, GLUE score

### Memory Reduction Method
- **Ablated Part**: Gradient projection approach
- **Action**: REPLACE
- **Replacement**: 
  - GaLore
  - LoRA
  - Full rank training
- **Metrics**: Memory usage (GB), Training loss, GLUE score

</div>