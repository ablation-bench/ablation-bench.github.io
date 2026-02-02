<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Emergent_Mixture_of_Experts__Can_Dense_Pre_trained_Transformers_Benefit_from_Emergent_Modular_Structures_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One important aspect that is not explicitly ablated in the paper is the reliance on pre-trained transformer weights to “externalize” emergent modularity. The current method extracts modular structures from pre-trained FFNs via constrained clustering, but it remains unclear whether these benefits are inherently due to the pre-training phase. Therefore, an ablation that compares the performance of EMoE applied on randomly initialized (i.e., non-pretrained) networks versus the standard pre-trained ones would help clarify whether emergent modularity is indeed a phenomenon induced by pre-training. 

A second potential ablation relates to the expert construction step. The paper uses a constrained clustering method to group similar key vectors into experts. However, it remains uninvestigated how sensitive the performance is to the choice of clustering algorithm. By replacing the current method with alternatives such as K-means clustering, hierarchical clustering, or even a random assignment of keys, one can assess whether the specific clustering technique is critical to reaping the benefits of EMoE.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Pre-training Ablation
- **Ablated Part**: Dependency on pre-trained weights for emergent modularity extraction in transformer FFNs
- **Action**: REPLACE
- **Replacement**: 
  - Random initialization
  - Pre-trained weights
- **Metrics**: ID Accuracy, OOD Accuracy, Friedman Rank

### Clustering Algorithm Ablation
- **Ablated Part**: Method used for partitioning FFN key vectors into experts
- **Action**: REPLACE
- **Replacement**: 
  - Constrained Clustering (current)
  - K-means Clustering
  - Hierarchical Clustering
  - Random Assignment
- **Metrics**: ID Accuracy, OOD Accuracy, Friedman Rank

</div>