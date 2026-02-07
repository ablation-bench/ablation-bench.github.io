<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Pooling_And_Attention__What_Are_Effective_Designs_For_LLM_Based_Embedding_Models_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Pooling And Attention: What Are Effective Designs For LLM-Based Embedding Models?" explores the effectiveness of different pooling and attention strategies for Large Language Model (LLM)-based embedding models. The authors conduct a large-scale experiment by training a series of LLM-based embedding models using the same training data and base model but differing in their pooling and attention strategies. The results show that there is no one-size-fits-all solution, and the effectiveness of pooling and attention strategies appears to be task-dependent.

The paper proposes a new pooling strategy, Multi-Layers Trainable Pooling, which transforms the outputs of all hidden layers, rather than just the last layer, using a cross-attention network. This method proves to be statistically superior in text similarity and retrieval tasks compared to existing pooling methods.

To further investigate the effectiveness of different pooling and attention strategies, we suggest two missing ablation studies:

1. Ablation study on the impact of the number of layers used in the Multi-Layers Trainable Pooling strategy. This study would help to understand how the number of layers affects the performance of the model and whether using all layers is necessary.
2. Ablation study on the effect of using different attention mechanisms, such as hierarchical attention or multi-head attention, in combination with the Multi-Layers Trainable Pooling strategy. This study would help to understand whether the choice of attention mechanism affects the performance of the model and whether the proposed pooling strategy is effective with different attention mechanisms.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: number of layers in Multi-Layers Trainable Pooling
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 2
  - 4
  - 8
- **Metrics**: STS, Retrieval, Classification, Clustering

### Ablation B
- **Ablated Part**: attention mechanism
- **Action**: REPLACE
- **Replacement**: 
  - hierarchical attention
  - multi-head attention
- **Metrics**: STS, Retrieval, Classification, Clustering

</div>