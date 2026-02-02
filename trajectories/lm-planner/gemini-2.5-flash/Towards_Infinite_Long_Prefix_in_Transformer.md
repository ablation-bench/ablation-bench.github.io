<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Towards_Infinite_Long_Prefix_in_Transformer

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Towards Infinite-Long Prefix in Transformer" proposes NTK-Attention, a parameter-efficient fine-tuning method that approximates attention with an ultra-long prefix using two trainable parameters, Z and k, derived from a theoretical analysis based on the Neural Tangent Kernel (NTK) framework. The method replaces the large prefix matrix P with a low-rank decomposed matrix Z (ZA * ZB) and a vector k in each attention layer.

The paper includes an ablation study in Appendix B.3 (summarized in Section 5) that investigates the sensitivity of the hyperparameters r (dimension of the feature mapping ϕ) and s (rank of the low-rank decomposition of Z) on a specific model (LLAMA-3.1-8B-Instruct) and dataset (WikiText-103). This ablation explores different combinations of r and s to understand their impact on performance and parameter count.

However, the existing ablation does not test the contribution of the core trainable components themselves or the effect of the low-rank approximation strategy for Z. Based on the method description, two key trainable components are introduced: the matrix Z (implemented as ZA * ZB) and the vector k. The low-rank decomposition of Z is presented as a practical implementation detail for efficiency.

Therefore, two important missing ablation studies are:

1.  **Ablating the trainable vector k:** The NTK-Attention algorithm (Algorithm 2) uses both Z and k in the denominator and numerator terms of the attention approximation. Removing k would test its necessity and contribution to the method's performance. This is a fundamental component to validate.
2.  **Ablating the low-rank decomposition of Z:** The paper uses a low-rank decomposition Z = ZA * ZB for parameter efficiency. While the existing ablation varies the rank 's', it doesn't compare the performance against using a full-rank Z (i.e., s=r) when computationally feasible (e.g., for smaller values of r like r=d). This would clarify if the low-rank structure itself has an impact on performance beyond just reducing the number of parameters.

These two ablations are crucial for understanding which parts of the proposed NTK-Attention mechanism are essential for its empirical performance, complementing the theoretical analysis and the hyperparameter sensitivity study already provided. They are ranked by their importance in validating the core trainable components of the proposed algorithm.

The metrics used in the paper for evaluating performance across different tasks are Accuracy (for SuperGLUE, Vision, and Math datasets) and Perplexity (for Language Modeling tasks). These metrics should be used for the suggested ablation studies to ensure comparability with the reported results.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablate trainable vector k
- **Ablated Part**: The trainable vector k in the NTK-Attention approximation formula.
- **Action**: REMOVE
- **Metrics**: Accuracy, Perplexity

### Full-rank Z vs Low-rank Z
- **Ablated Part**: The low-rank decomposition of the trainable matrix Z (ZA * ZB).
- **Action**: REPLACE
- **Replacement**: 
  - Full-rank matrix Z (r x d)
- **Metrics**: Accuracy, Perplexity

</div>