<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/BA_LoRA__Bias_Alleviating_Low_Rank_Adaptation_to_Mitigate_Catastrophic_Inheritance_in_Large_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The BA-LoRA paper introduces three crucial regularization terms (consistency, diversity, and SVD) and adopts a SVD‐based initialization (inherited from PiSSA) for adapter matrices to mitigate catastrophic inheritance. However, two important design choices are not explicitly ablated:
1. The impact of the SVD‐based initialization strategy versus a standard random initialization has not been isolated. Replacing the SVD-based initialization with a random initialization in the low-rank adapters would help quantify how much the initialization method alone contributes to bias mitigation, convergence speed, and downstream performance.
2. For the consistency regularizer on NLU tasks, the paper employs an MSE loss between normalized logits. An ablation that replaces this loss with an alternate similarity measure (e.g., cosine similarity) would reveal if the choice of loss function significantly affects the preservation of pre-trained knowledge and overall performance.
These studies would rank highly in importance since they target fundamental components of BA-LoRA’s design and could offer deeper insight into which design choices are most beneficial for alleviating catastrophic inheritance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Adapter Initialization Ablation
- **Ablated Part**: SVD-based initialization of the low-rank adapter matrices
- **Action**: REPLACE
- **Replacement**: 
  - Random Initialization
- **Metrics**: NLU metrics (accuracy, Matthews correlation, Pearson correlation), NLG metrics (Accuracy, Pass@1, GPT-4 Evaluation

### Consistency Loss Ablation
- **Ablated Part**: Consistency regularizer loss function for NLU tasks
- **Action**: REPLACE
- **Replacement**: 
  - Cosine Similarity Loss
  - KL Divergence Loss
- **Metrics**: GLUE benchmark scores (accuracy, F1, Matthews correlation), OOD performance on GLUE-X

</div>