<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Pooling_And_Attention__What_Are_Effective_Designs_For_LLM_Based_Embedding_Models_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Pooling And Attention: What Are Effective Designs For LLM-Based Embedding Models?" explores various pooling and attention strategies for LLM-based embedding models. The authors conduct a series of experiments using different combinations of pooling and attention strategies, such as EOS-last token pooling, mean pooling, trainable pooling layers, and bidirectional attention. They also propose a new pooling strategy called Multi-Layers Trainable Pooling, which leverages hidden states from all layers of the LLM.

The existing ablation studies in the paper focus on comparing different pooling and attention strategies under controlled conditions, using the same base model and training data. The authors evaluate the performance of these strategies on various tasks, including text similarity, information retrieval, clustering, and classification, using the MTEB benchmark. They also conduct statistical significance tests to ensure the robustness of their findings.

However, there are some potential areas for further exploration that are not covered in the existing ablation studies. One such area is the impact of different types of attention mechanisms beyond the causal and bidirectional attention used in the paper. Another area is the exploration of different configurations of the trainable pooling layer, such as varying the number of layers or the size of the hidden states used in the pooling process.

Based on these observations, I suggest two missing ablation studies that could provide additional insights into the design of LLM-based embedding models.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Attention Mechanism
- **Action**: REPLACE
- **Replacement**: 
  - Self-attention
  - Cross-attention
  - Multi-head attention
- **Metrics**: STS, Retrieval, Classification, Clustering

### Ablation Study 2
- **Ablated Part**: Trainable Pooling Layer Configuration
- **Action**: REPLACE
- **Replacement**: 
  - Varying number of layers
  - Different hidden state sizes
- **Metrics**: STS, Retrieval, Classification, Clustering

</div>