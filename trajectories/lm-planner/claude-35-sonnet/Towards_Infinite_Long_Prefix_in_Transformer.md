<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Towards_Infinite_Long_Prefix_in_Transformer

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on my analysis of the paper, there are two important ablation studies missing that could help validate key components of the proposed method:

1. The first missing ablation study should examine the impact of the feature mapping function ϕ used in NTK-Attention. The paper uses a first-order polynomial method for ϕ but doesn't ablate this choice. This is important since ϕ is critical for approximating the infinite-length prefix.

2. The second missing ablation should investigate the effect of the low-rank approximation used for the Z matrix in NTK-Attention. While the paper uses low-rank matrices ZA and ZB to approximate Z for parameter efficiency, it doesn't study how different rank values affect the tradeoff between efficiency and performance.

The paper already includes ablations studying:
- Sensitivity of hyperparameters r and s
- Computational costs comparison between NTK-Attention and standard prefix attention
- Performance comparison with baselines like LoRA and P-Tuning V2

But it's missing these two key ablations that would help validate core design choices in the method.

The metrics used in the paper include:
- Accuracy for classification tasks
- Perplexity (PPL) for language modeling
- Cross-entropy loss for WikiText-103
- Runtime and memory usage for efficiency analysis

I'll format the suggested ablations in JSONL format below.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Feature Mapping Ablation
- **Ablated Part**: Feature mapping function ϕ used in NTK-Attention
- **Action**: REPLACE
- **Replacement**: 
  - Second-order polynomial mapping
  - RBF kernel mapping
  - Neural network mapping
- **Metrics**: Accuracy, Perplexity, Cross-entropy loss, Runtime

### Low-rank Matrix Ablation
- **Ablated Part**: Low-rank approximation of Z matrix using ZA and ZB
- **Action**: REPLACE
- **Replacement**: 
  - Full-rank Z matrix
  - Different rank values for ZA and ZB (25%, 50%, 75% of full rank)
- **Metrics**: Accuracy, Perplexity, Cross-entropy loss, Memory usage

</div>