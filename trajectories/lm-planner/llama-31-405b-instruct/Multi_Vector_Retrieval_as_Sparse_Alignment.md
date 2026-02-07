<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Multi_Vector_Retrieval_as_Sparse_Alignment

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Multi-Vector Retrieval as Sparse Alignment" proposes a novel multi-vector retrieval model called ALIGNER, which learns sparsified pairwise alignments between query and document tokens and per-token unary saliences reflecting their relative importance for retrieval. The model achieves strong performance on both zero-shot and few-shot document retrieval tasks while improving the run-time and storage complexity of multi-vector retrieval.

To further analyze the effectiveness of ALIGNER, we suggest two missing ablation studies:

1. **Ablation of Unary Saliences**: The paper highlights the importance of unary saliences in pruning unimportant tokens and improving retrieval efficiency. However, it would be interesting to see the impact of removing unary saliences from the model. This ablation study would help understand the contribution of unary saliences to the overall performance of ALIGNER.

2. **Ablation of Pairwise Alignments**: The paper proposes adapting pairwise alignments with a few examples (≤ 8) to improve performance on target tasks. An ablation study that removes pairwise alignments and only uses unary saliences would help understand the importance of pairwise alignments in the model.

These ablation studies would provide a more comprehensive understanding of the components of ALIGNER and their contributions to its performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Unary Saliences
- **Ablated Part**: Unary Saliences
- **Action**: REMOVE
- **Metrics**: nDCG@10, MRR@10

### Ablation of Pairwise Alignments
- **Ablated Part**: Pairwise Alignments
- **Action**: REMOVE
- **Metrics**: nDCG@10, MRR@10

</div>