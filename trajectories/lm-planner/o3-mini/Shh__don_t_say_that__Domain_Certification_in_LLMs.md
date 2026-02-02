<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Shh__don_t_say_that__Domain_Certification_in_LLMs

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We identified two key components in VALID that were not systematically ablated in the paper. First, the rejection sampling procedure employs a length‐normalized log likelihood ratio (i.e. using a threshold of k×N₍ʸ₎) to decide whether to accept a sample. Although the paper motivates this linear normalization to counteract the exponential decay of likelihoods with increasing sequence length, it does not compare alternative normalization strategies. An ablation study that replaces the current linear scaling with other strategies (e.g. no normalization, sub‐linear such as √N, or super‐linear such as N^1.5) would help quantify the impact on the false rejection rate (FRR), the atomic certificate (εʸ‐AC) and the overall domain certificate (ε-DC), as well as on the downstream benchmark performance (PubMedQA/MMLU accuracy).
Second, the VALID certification leverages the ratio between L(y|x) and the guide model’s likelihood G(y) as its divergence measure. While the theoretical discussion touches on Rényi divergence, the implementation relies on the normalized likelihood ratio. A missing ablation study would be to replace this design choice with alternative divergence measures (for example, using unnormalized likelihood ratios, Kullback–Leibler divergence, JS divergence, or even energy‐based scores) to evaluate if these alternatives can yield tighter certificates or better trade-offs between safety (OCC detection and FRR) and task performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Length Normalization Strategy
- **Ablated Part**: The scaling strategy used in the rejection threshold (currently k * N_y) for length normalization in VALID
- **Action**: REPLACE
- **Replacement**: 
  - No normalization
  - Sub-linear normalization (e.g., sqrt(N_y))
  - Super-linear normalization (e.g., N_y^1.5)
- **Metrics**: FRR, ε^y-AC, ε-DC, Benchmark Task Accuracy

### Ablation: Alternative Divergence Measures
- **Ablated Part**: The choice of divergence measure for certification, specifically the use of a length-normalized log-likelihood ratio between L and G
- **Action**: REPLACE
- **Replacement**: 
  - Unnormalized likelihood ratio
  - KL divergence
  - JS divergence
  - Energy-based score
- **Metrics**: ε^y-AC, ε-DC, FRR, OOD Detection Rate, Benchmark Task Accuracy

</div>