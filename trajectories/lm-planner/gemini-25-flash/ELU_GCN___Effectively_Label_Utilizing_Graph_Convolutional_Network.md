<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/ELU_GCN___Effectively_Label_Utilizing_Graph_Convolutional_Network

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes ELU-GCN, a two-stage framework for effectively utilizing label information in Graph Convolutional Networks. The two main stages are: 1) learning an ELU-graph structure that enables GCNs to effectively utilize label information, and 2) designing a graph contrastive learning mechanism that explores consistency and mutually exclusive information between the learned ELU graph and the original graph. The final objective function combines a supervised classification loss (using a fused prediction from both graph views) and the contrastive loss.

The paper includes an ablation study in Table 2, which compares:
1.  GCN (baseline using the original graph).
2.  GCN + ELU graph (using the learned ELU graph, likely replacing the original graph in the GCN layer, without the contrastive loss or prediction fusion).
3.  +Lcon (the full ELU-GCN model, which uses the ELU graph, the original graph, the contrastive loss, and prediction fusion).

This existing ablation demonstrates the overall contribution of the ELU graph learning and the contrastive loss component. However, it does not fully isolate the impact of specific design choices within the proposed framework. Two such choices are particularly important and are not clearly ablated:

1.  **Pseudo-label Initialization:** The method describes expanding the initial limited labels with pseudo-labels of ELU nodes (Algorithm 1, Section D.2). This is a form of data augmentation that provides more labeled data for the ELU graph learning process. It is crucial to understand how much of the performance gain is attributable to this increased amount of training data versus the core mechanism of learning the ELU graph structure itself. An ablation removing this pseudo-labeling step would clarify its contribution.
2.  **Prediction Fusion:** The final classification loss (Eq. 11) uses a weighted fusion of predictions obtained from processing the data through GCN layers using both the original graph and the learned ELU graph. While the contrastive loss encourages consistency between representations from both views, the final prediction explicitly combines them. The existing ablation compares a model using only the ELU graph view (GCN + ELU graph, without Lcon or fusion) to the full model (with Lcon and fusion). It doesn't isolate the effect of the fusion strategy itself when the contrastive loss is active. An ablation comparing the full fused model against variants that use only one view's prediction (e.g., only the ELU graph view's prediction) would show the benefit of combining information at the output layer.

Based on their potential impact on the model's performance and the clarity they would bring to the contribution of specific components, these two ablations are suggested as important missing experiments.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Pseudo-label Initialization
- **Ablated Part**: Initialization of label matrix with pseudo-labels of ELU nodes
- **Action**: REMOVE
- **Metrics**: Accuracy

### Ablation on Prediction Fusion
- **Ablated Part**: Fusion of predictions from original and ELU graph views in the final classification loss
- **Action**: REPLACE
- **Replacement**: 
  - Using only the ELU graph view prediction
- **Metrics**: Accuracy

</div>