<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Enriching_Knowledge_Distillation_with_Intra_Class_Contrastive_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes enriching knowledge distillation by incorporating an intra-class contrastive loss (L_Intra) during teacher training. This loss encourages diversity within the embeddings of samples belonging to the same class, aiming to provide richer soft labels for the student model. The initial teacher loss is a combination of standard cross-entropy (L_CE) and L_Intra, weighted by a parameter λ.

A key challenge identified by the authors is that the standard L_Intra can cause training instability and slow convergence, particularly for samples that the teacher model is not yet confident about. To address this, they introduce a margin-based approach, where L_Intra is only applied to samples whose margin (confidence in the ground truth class vs. the next highest class) exceeds a threshold δ. This modified L_Intra is used in the final teacher training objective. The paper also mentions a pipeline-based caching mechanism to handle limited negative samples due to batch size constraints, which is presented as a practical implementation detail.

The paper provides theoretical analysis on the impact of λ on the ratio of intra-class and inter-class losses/distances. Experimental results compare the proposed method ("Ours", which includes the margin and pipeline) and "Ours+RKD" against several baseline distillation methods, showing improvements in Top-1 accuracy on CIFAR-100, Tiny ImageNet, and CIFAR-10.

While the paper demonstrates the effectiveness of the overall method, it lacks detailed ablation studies on the specific contributions of its key components. Specifically, the impact of the margin threshold (δ) and the intra-class loss weight (λ) are not experimentally evaluated.

1.  **Ablation on Margin Threshold (δ):** The introduction of the margin is a crucial modification to the core intra-class contrastive loss, intended to improve stability and convergence. An ablation study varying the margin threshold δ (including setting it to 0, which effectively removes the margin filtering) would directly assess the necessity and effectiveness of this component. It would show whether the margin is indeed critical for performance or stability, or if the base L_Intra (perhaps with careful tuning) could suffice. This is highly important as it validates a core design choice made to mitigate practical issues.

2.  **Ablation on Intra-Class Loss Weight (λ):** The parameter λ controls the balance between the standard classification objective (L_CE) and the proposed intra-class diversity objective (L_Intra). The theoretical analysis highlights λ's role in controlling distance ratios. An experimental ablation varying λ would demonstrate its practical impact on the student's final performance. It would show the sensitivity of the method to this hyperparameter and help understand the trade-off between focusing on inter-class separation (driven by L_CE) and intra-class diversity (driven by L_Intra). While the authors state a range for λ, showing results for different values would provide empirical support for their choice and illustrate the performance landscape.

These two ablations are the most critical missing experiments because they directly evaluate the contribution and sensitivity of the two main novel components/parameters introduced in the teacher training objective (the form of L_Intra and its weight λ). The pipeline mechanism, while useful, is more of an implementation strategy than a fundamental algorithmic component affecting the loss function itself.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablate Margin Threshold
- **Ablated Part**: Margin threshold (δ) for applying intra-class contrastive loss
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.1
  - 0.5
  - 0.9
- **Metrics**: Top-1 Accuracy

### Ablate Intra-Class Loss Weight
- **Ablated Part**: Weight (λ) of the intra-class contrastive loss in the teacher objective
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.005
  - 0.01
  - 0.03
  - 0.05
  - 0.1
- **Metrics**: Top-1 Accuracy

</div>