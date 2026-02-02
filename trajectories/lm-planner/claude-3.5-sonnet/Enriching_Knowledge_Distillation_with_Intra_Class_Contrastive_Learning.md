<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Enriching_Knowledge_Distillation_with_Intra_Class_Contrastive_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes incorporating intra-class contrastive loss during teacher training to enrich the intra-class information contained in soft labels. The key components are:

1. Intra-class contrastive loss (Eq. 4) - Uses augmented samples as positive pairs and other samples from same class as negative pairs
2. Margin loss integration - Only applies intra-class loss when margin exceeds threshold δ (Eq. 7)
3. Pipeline-based caching mechanism for memory efficiency

Looking at the ablation studies in the paper:
- They compare against baseline KD and other SOTA methods
- They show results with and without RKD integration
- However, they don't ablate the key novel components of their method

Key missing ablations:
1. The margin threshold δ is a critical hyperparameter that determines when to apply the intra-class loss, but there's no study of its impact
2. The pipeline-based caching mechanism is introduced to improve training stability, but its effectiveness is not validated

I'll focus on these two most important missing ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Margin Threshold Ablation
- **Ablated Part**: margin threshold δ in Eq. 7
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.2
  - 0.4
  - 0.6
  - 0.8
- **Metrics**: Top-1 accuracy, Training stability (loss variance), Convergence speed (epochs to converge)

### Pipeline Caching Ablation
- **Ablated Part**: pipeline-based caching mechanism
- **Action**: REMOVE
- **Metrics**: Top-1 accuracy, GPU memory usage, Training stability (loss variance)

</div>