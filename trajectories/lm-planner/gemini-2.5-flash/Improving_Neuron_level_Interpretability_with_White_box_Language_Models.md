<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Improving_Neuron_level_Interpretability_with_White_box_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Improving Neuron-level Interpretability with White-box Language Models" introduces CRATE, a transformer-like architecture designed with built-in sparse coding to enhance neuron-level interpretability. The core idea is to embed sparse coding directly into the model architecture, specifically within the Iterative Shrinkage-Thresholding Algorithm (ISTA) block, which replaces the standard Feed-Forward Network (FFN) or MLP block found in traditional transformers like GPT. The paper also utilizes a Multi-Head Subspace Self-Attention (MSSA) block, a variant of standard multi-head attention.

The paper presents extensive experiments comparing CRATE to GPT-2 and GPT-2 with post-hoc Sparse Auto-Encoders (SAEs) across various model sizes and layers, demonstrating improved interpretability metrics (OpenAI Top-and-Random, OpenAI Random-only, Anthropic) while maintaining comparable next-token prediction performance. It also analyzes factors like training progress and parameter count to argue that the interpretability gain is not merely a side effect of performance or size differences. The paper also briefly mentions the number of ISTA iterations (`t=2`) and the overcompleteness factor (`n=4`) as design choices.

However, the paper lacks ablation studies on the core components of the CRATE architecture itself to isolate their specific contributions to the observed interpretability gains. While the comparison to GPT is informative, it doesn't tell us *which* aspects of CRATE's design are responsible. The two most critical components differentiating CRATE from a standard transformer are the ISTA block (implementing the built-in sparse coding) and the MSSA block. The ISTA block, in particular, is central to the paper's hypothesis about embedding sparsity.

Therefore, two important missing ablation studies are:

1.  **Replacing the ISTA block with a standard MLP:** This directly tests whether the specific structure and mechanism of the ISTA block, designed for sparse coding, are necessary for the improved interpretability, or if a standard MLP with similar capacity would yield comparable results. This is crucial because the ISTA block is the primary mechanism proposed for achieving built-in sparsity.
2.  **Ablating the Sparsification Regularizer (λ) within the ISTA block:** The L1 regularization term (λ) in the ISTA objective (Equation 1, 6) is explicitly designed to promote sparsity. Removing or varying this term would demonstrate the extent to which the explicit sparsity objective contributes to the neuron-level interpretability, as opposed to other aspects of the ISTA block's structure or the overall training process.

These two ablations are ranked by importance based on their direct relevance to the paper's core claims about built-in sparse coding via the ISTA block. Ablating the ISTA block entirely is arguably the most significant test of the architectural change, while ablating the sparsity regularizer tests the necessity of the explicit sparsity *objective* within that block. Both are vital for understanding the causal link between CRATE's design and its interpretability. The metrics used in the paper (validation loss and the three interpretability scores) should be used to evaluate these ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### ISTA Block Replacement
- **Ablated Part**: Iterative Shrinkage-Thresholding Algorithm (ISTA) block
- **Action**: REPLACE
- **Replacement**: 
  - Standard Feed-Forward Network (MLP) block
- **Metrics**: Validation Loss, OpenAI Top-and-Random, OpenAI Random-only, Anthropic

### Sparsification Regularizer Ablation
- **Ablated Part**: Sparsification regularizer (lambda) in the ISTA block objective
- **Action**: REPLACE
- **Replacement**: 
  - 0
  - lambda/2
  - lambda*2
- **Metrics**: Validation Loss, OpenAI Top-and-Random, OpenAI Random-only, Anthropic

</div>