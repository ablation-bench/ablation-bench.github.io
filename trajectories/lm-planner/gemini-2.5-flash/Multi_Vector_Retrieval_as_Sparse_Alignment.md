<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Multi_Vector_Retrieval_as_Sparse_Alignment

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Multi-Vector Retrieval as Sparse Alignment" introduces ALIGNER, a multi-vector retrieval model that factorizes the query-document similarity into pairwise token alignments and per-token unary saliences. The core idea is that sparse alignments and sparse token saliences are beneficial for both accuracy and efficiency.

The paper presents several ablation studies:
1.  **Pairwise Alignment Strategy:** They explore different strategies for determining pairwise alignment (Top-k, Top-p) at inference time and show that adapting the strategy improves performance on different tasks (Table 3, Figure 4, Tables 7-12). They also compare training with different fixed strategies (Appendix A.4, Table 6, Figure 4) and a differentiable alignment method (Appendix A.2, Table 6, Table 13).
2.  **Few-shot Alignment Adaptation:** They demonstrate the effectiveness of using a few examples to select the best pairwise alignment strategy (Table 2, Figure 5).
3.  **Unary Salience for Pruning:** They show that using learned unary saliences to prune query and document tokens significantly improves efficiency with minimal performance loss *after* the model has been trained (Figure 6, Figure 7).
4.  **Unary Salience Learning Method:** They compare their entropy-regularized linear programming approach for learning unary salience against alternatives like simple ReLU gate, hard Top-k selection, and L1 regularization, showing their method performs well, especially at higher pruning ratios (Figure 6).
5.  **Model Scaling:** They show that ALIGNER benefits from scaling up the base language model (Figure 3, Table 2, Tables 7-10).

While the paper effectively demonstrates the *utility* of the learned unary saliences for post-training pruning and compares different *methods* for learning salience sparsity, a key missing ablation is the impact of the unary salience component *during training*. The model is trained end-to-end with the objective that includes the factorized alignment matrix A = A˜ ⊙ (u^q ⊗ u^d). Does the process of jointly learning sparse unary saliences alongside pairwise alignments contribute to better overall retrieval performance *before* any pruning is applied? Or is the primary benefit of the unary salience mechanism solely for enabling efficient pruning *after* training? An ablation where the model is trained *without* the unary salience component (effectively fixing u^q and u^d to non-sparse values like 1) would directly answer this question about the contribution of the learned salience during the training phase itself. This is the most important missing ablation.

Another aspect related to unary salience is the sensitivity to the training-time sparsity ratios (α^q, α^d). The paper mentions these are set empirically (50% for query, 40% for document). Ablating these hyperparameters during training would reveal how sensitive the model's final performance is to the specific level of sparsity enforced on the saliences during optimization. This is also a valuable ablation for understanding the robustness and hyperparameter tuning requirements of the method.

Based on this analysis, the two most important missing ablation studies are:
1.  Training the model without the unary salience component.
2.  Investigating the sensitivity of the model's performance to the training-time sparsity ratios for unary salience.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Unary Salience Training
- **Ablated Part**: Learning and application of unary salience (u^q, u^d) during training
- **Action**: REMOVE
- **Metrics**: nDCG@10, MRR@10

### Sensitivity to Unary Salience Training Sparsity
- **Ablated Part**: Training-time sparsity ratios for unary salience (alpha_q, alpha_d)
- **Action**: REPLACE
- **Replacement**: 
  - {'alpha_q': 0.2, 'alpha_d': 0.4}
  - {'alpha_q': 0.5, 'alpha_d': 0.2}
  - {'alpha_q': 0.5, 'alpha_d': 0.6}
  - {'alpha_q': 0.8, 'alpha_d': 0.4}
- **Metrics**: nDCG@10, MRR@10

</div>