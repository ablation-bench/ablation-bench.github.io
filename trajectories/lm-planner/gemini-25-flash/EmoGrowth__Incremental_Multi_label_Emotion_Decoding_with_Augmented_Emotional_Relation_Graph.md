<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/EmoGrowth__Incremental_Multi_label_Emotion_Decoding_with_Augmented_Emotional_Relation_Graph

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "EmoGrowth: Incremental Multi-label Emotion Decoding with Augmented Emotional Relation Graph" proposes the Augmented Emotional Semantics Learning (AESL) framework to address multi-label class incremental emotion decoding, specifically tackling past- and future-missing partial label problems. The core components of AESL are:
1.  Augmented Emotional Relation Graph (ERG) with Graph-based Label Disambiguation (AEG-D): Addresses past-missing partial labels by constructing an augmented ERG and refining soft labels.
2.  Emotional Semantics Learning (ESL): Learns emotion embeddings from the ERG using a Graph Autoencoder (GAE) with a pairwise decoder loss (Lle).
3.  Semantic-Guided Feature Decoupling: Uses learned emotion embeddings to guide instance feature extraction.
4.  Relation-Based Knowledge Distillation (RKD): Addresses future-missing partial labels by aligning the model's feature space with both an affective dimension space (Lkd_aff) and the old model's feature space (Lkd_model).

The paper includes an ablation study (Section 4.2) evaluating the contribution of several components:
*   `w/o ES-L&LD`: Removes the combined ESL and Label Disambiguation modules.
*   Variations of `w/o ES-L&LD` replacing the removed part with alternative embeddings (+SE, +LE, +AD).
*   `w/o LD`: Removes only the Label Disambiguation part of AEG-D.
*   `w/o RKD`: Removes the entire RKD module.
*   `w/o RKD, + LR`: Replaces RKD with a linear regressor.

While these ablations cover the major modules, there are opportunities for more fine-grained analysis of key mechanisms. Based on the method description and existing ablations, two important missing ablation studies are identified:

1.  **Ablation of Individual RKD Teachers:** The RKD module is a crucial part of AESL, designed to mitigate the future-missing partial label problem by distilling knowledge from *two* sources: affective dimensions and the old model. The total RKD loss is a weighted sum of Lkd_aff and Lkd_model. The paper ablates the removal of the entire RKD module (`w/o RKD`) and performs a parameter sensitivity analysis for λ2 (weight of Lkd_aff) while fixing λ1 (weight of Lkd_model) to 1. However, it does not explicitly ablate the contribution of each teacher individually. An ablation study comparing the performance when only using Lkd_aff or only using Lkd_model would clearly demonstrate the necessity and relative importance of each knowledge source for effective knowledge distillation in this MLCIL setting.

2.  **Ablation of ESL Graph Reconstruction Loss:** The Emotional Semantics Learning (ESL) module learns emotion embeddings from the augmented ERG using a GAE trained with a pairwise decoder loss (Lle) that reconstructs the graph structure. The `w/o ES-L&LD` ablation removes this entire learning process. However, it's unclear how important the *explicit* objective of reconstructing the graph structure via the Lle loss is, compared to simply using the GIN encoder and letting it be trained implicitly by the downstream classification and RKD losses. Removing the Lle term from the total loss would isolate the contribution of this specific graph-based training objective within the ESL module.

These two ablations are important because they probe the specific mechanisms designed to address the core challenges (partial labels, catastrophic forgetting) and contribute to the model's performance, providing deeper insight into why AESL is effective. The metrics used in the main results (mAP, maF1, miF1 for both average and last task performance) should be reported for these ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of RKD Teacher Type
- **Ablated Part**: Relation-Based Knowledge Distillation (RKD) loss (Lkd)
- **Action**: REPLACE
- **Replacement**: 
  - Lkd_aff only
  - Lkd_model only
- **Metrics**: Avg. Acc (mAP), Last Acc (mAP), Avg. Acc (maF1), Last Acc (maF1), Avg. Acc (miF1), Last Acc (miF1)

### Ablation of ESL Graph Reconstruction Loss
- **Ablated Part**: Pairwise decoder loss (Lle) for graph reconstruction in the Emotional Semantics Learning (ESL) module
- **Action**: REMOVE
- **Metrics**: Avg. Acc (mAP), Last Acc (mAP), Avg. Acc (maF1), Last Acc (maF1), Avg. Acc (miF1), Last Acc (miF1)

</div>