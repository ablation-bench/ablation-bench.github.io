<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Annotation_Efficient_Language_Model_Alignment_via_Diverse_and_Representative_Response_Texts

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two critical ablation studies that are missing from the current experiments. First, the AEPO method relies crucially on a dissimilarity function (currently defined as “1 – cosine similarity”) to compute both the representativeness and diversity terms in its objective. However, it remains unclear how sensitive AEPO is to the choice of this metric. Evaluating alternative distance measures (such as Euclidean distance or Manhattan distance) would help assess the robustness of the selection strategy and its impact on alignment performance. Second, the current experiments fix the subsample size (i.e. the number of responses per instruction selected for annotation) to k = 2. Varying this parameter would shed light on the trade-offs between annotation cost, diversity of the selected responses, and the resulting model performance. In both cases, we would report metrics that are used in the paper – including reward scores (e.g., Eurus, OASST), win rate against the SFT baseline, and supplementary diversity/quality measures (e.g., distinct‐n and pairwise Sentence BERT similarity) – so that we can quantify the changes in alignment performance and dataset quality.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Alternative Dissimilarity Metrics
- **Ablated Part**: The dissimilarity function used in the AEPO objective (currently set as 1 - cosine similarity)
- **Action**: REPLACE
- **Replacement**: 
  - euclidean distance
  - manhattan distance
  - cosine distance (baseline)
- **Metrics**: Eurus reward score, OASST reward score, win rate, diversity metrics (pairwise SentenceBERT similarity, distinct-n)

### Ablation 2: Varying Annotation Budget per Instruction
- **Ablated Part**: The fixed number of subsampled responses (k, currently set to 2) for preference annotation
- **Action**: REPLACE
- **Replacement**: 
  - k = 1
  - k = 2
  - k = 4
- **Metrics**: win rate, reward scores (Eurus, OASST), diversity quality metrics (pairwise SentenceBERT similarity, distinct-n), annotation cost

</div>