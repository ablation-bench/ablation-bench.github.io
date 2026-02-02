<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Advancing_Beyond_Identification__Multi_bit_Watermark_for_Large_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Advancing Beyond Identification: Multi-bit Watermark for Large Language Models" proposes MPAC, a method for embedding multi-bit watermarks in LLM generated text. The method extends zero-bit watermarking by allocating tokens to message positions and partitioning the vocabulary into 'r' color lists. Key components include a hashing scheme based on previous tokens used for both position allocation and vocabulary permutation, the application of a bias (δ) to favored colorlist tokens, and a decoding strategy based on counting tokens per colorlist per position.

The paper includes several ablation studies and analyses, such as the effect of bias magnitude (δ), greenlist ratio (γ) and radix (r), token length (T) and bit width (b), robustness to attacks (copy-paste, paraphrasing), performance across different models and datasets, comparison of LeftHash (h=1) and SelfHash (h=4) hashing schemes, the effectiveness of list decoding, and preliminary results on feedback mechanisms.

Based on the method description and the existing ablations, two important missing ablation studies are identified:

1.  **Hashing Scheme Role:** The paper compares LeftHash (h=1) and SelfHash (h=4) but uses the *same* scheme for *both* the position allocation step and the vocabulary permutation step within a single experiment run. The discussion in Appendix A.3 suggests that different hashing schemes might be better suited for different roles (robustness for position allocation, quality for vocabulary partitioning). An ablation studying the effect of using different hashing schemes for these two distinct roles within MPAC is missing and would provide valuable insight into the specific contributions of each hashing scheme to different aspects of performance (bit accuracy, robustness, quality, latency).

2.  **Position Sampling Strategy:** At each token generation step, MPAC samples a *single* message position `p` uniformly from the `~b` possible positions. This per-token, single-position allocation is a core design choice. The paper shows that deterministic allocation is fragile, justifying the hashing-based sampling, but it doesn't explore alternative *sampling strategies* for `p`. Ablating the uniform sampling strategy to explore non-uniform distributions (e.g., favoring certain positions, or attempting to counteract observed non-uniformity like in Table 2) or even sampling *multiple* positions per token could reveal whether the uniform, single-position sampling is optimal or if other strategies could improve performance or robustness.

These two ablations are crucial for a deeper understanding of how the core mechanisms of MPAC contribute to its overall performance and robustness. They investigate the specific roles of the hashing scheme and the fundamental strategy for allocating tokens to message bits. The metrics used in the paper (bit accuracy, detection performance, text quality, latency) are appropriate for evaluating these ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Hashing Scheme Role Ablation
- **Ablated Part**: Using the same hashing scheme (LeftHash or SelfHash) for both position allocation and vocabulary permutation.
- **Action**: REPLACE
- **Replacement**: 
  - LeftHash for position allocation and SelfHash for vocabulary permutation
  - SelfHash for position allocation and LeftHash for vocabulary permutation
- **Metrics**: Bit Accuracy, List Decoded Bit Accuracy, AUROC, TPR, Perplexity (PPL), Semantic Similarity (P-SP), Encoding Latency, Decoding Latency

### Position Sampling Strategy Ablation
- **Ablated Part**: Uniform sampling of a single message position per token.
- **Action**: REPLACE
- **Replacement**: 
  - Non-uniform sampling (e.g., favoring lower indices)
  - Sampling multiple positions per token (e.g., k positions)
- **Metrics**: Bit Accuracy, List Decoded Bit Accuracy, AUROC, TPR, Perplexity (PPL), Semantic Similarity (P-SP)

</div>