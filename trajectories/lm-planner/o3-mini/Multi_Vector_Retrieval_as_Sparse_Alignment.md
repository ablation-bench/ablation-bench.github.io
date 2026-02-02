<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Multi_Vector_Retrieval_as_Sparse_Alignment

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We observed that ALIGNER’s performance hinges on its two main components: pairwise alignments and the unary salience module. Although the paper provides extensive experiments on different alignment variants and comparisons between various methods to achieve sparsity (e.g., using entropy-regularized linear programming vs. hard thresholding or L1 regularization), it does not include an ablation where the learned unary salience mechanism is completely removed (or replaced by a uniform weighting). Such an experiment would help quantify the direct contribution of the unary salience in guiding token selection, interpretability, and token pruning efficiency. Moreover, while the paper fixes the training sparsity ratios (for example α_q = 50% and α_d = 40%), it does not explore how varying these constraints during training might affect retrieval accuracy versus efficiency trade-offs. Investigating this sensitivity would provide deeper insights into optimal sparsity settings. These two ablations are therefore highly important to better attribute performance gains to these major design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Unary Salience Removal Ablation
- **Ablated Part**: Learned unary salience gating mechanism that weighs token importance in the sparse alignment
- **Action**: REPLACE
- **Replacement**: 
  - uniform weights (i.e., set all token weights to 1)
- **Metrics**: nDCG@10, MRR@10, Index Size Reduction

### Unary Sparsity Constraint Ablation
- **Ablated Part**: Training sparsity constraint (α) used in the entropy-regularized linear programming for learning unary saliences
- **Action**: REPLACE
- **Replacement**: 
  - 20%
  - 40%
  - 60%
- **Metrics**: nDCG@10, MRR@10, Pruned Token Ratio

</div>