<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Knowledge_Consistent_Dialogue_Generation_with_Language_Models_and_Knowledge_Graphs

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One key component of SURGE is its end‐to‐end joint training of the subgraph retriever and the dialogue generator. Although the paper already compares different retrieval methods (e.g., dense, sparse, random) and different graph encoding variants, it does not explicitly investigate the importance of allowing the retriever and generator to be trained jointly. Freezing the retriever—thereby decoupling its training from that of the generator—could shed important light on how much the integrated joint training contributes to generating knowledge‐consistent responses (as measured by KQA, BLEU, and ROUGE). 

Another component that remains under-explored is the sensitivity of the marginalization process to the number of subgraph samples (k) used in approximating the latent variable integration. While the default k is set to 4, varying k (for instance, testing values 1, 4, 8, or 16) could affect both the retrieval quality and generation performance. Studying this ablation would provide insights into the trade-off between computational efficiency and performance in knowledge-grounded dialogue generation.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Fixed Retriever (No Joint Training)
- **Ablated Part**: End-to-end joint training of the subgraph retriever and the response generator
- **Action**: REMOVE
- **Metrics**: KQA EM, KQA F1, BLEU, ROUGE

### Ablation: Subgraph Sample Size Sensitivity
- **Ablated Part**: Number of subgraph samples (k) used for marginalizing over retrieved subgraphs during training
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 4
  - 8
  - 16
- **Metrics**: KQA EM, KQA F1, BLEU, ROUGE

</div>