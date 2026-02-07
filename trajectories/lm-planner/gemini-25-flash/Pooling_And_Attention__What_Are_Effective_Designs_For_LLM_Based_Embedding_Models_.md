<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Pooling_And_Attention__What_Are_Effective_Designs_For_LLM_Based_Embedding_Models_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Pooling And Attention: What Are Effective Designs For LLM-Based Embedding Models?" conducts a systematic study comparing different pooling and attention strategies for fine-tuning LLMs as embedding models. The authors evaluate five combinations of existing strategies and propose a new method called Multi-Layers Trainable Pooling, which utilizes hidden states from all layers of the LLM.

The existing experiments compare:
1.  EOS-Last Token Pooling + Causal Attention (Model 1)
2.  Last-Layer Trainable Pooling + Causal Attention (Model 2)
3.  Multi-Layers Trainable Pooling + Causal Attention (Model 3)
4.  Last-Layer Trainable Pooling + Bidirectional Attention (Model 4)
5.  Multi-Layers Trainable Pooling + Bidirectional Attention (Model 5)

These comparisons allow the authors to analyze the impact of different pooling strategies under causal attention (Model 1 vs 2 vs 3), different pooling strategies under bidirectional attention (Model 4 vs 5), and different attention strategies for trainable pooling (Model 2 vs 4 and Model 3 vs 5). They also perform a robustness check using a smaller base model (Qwen2-0.5B).

The proposed Multi-Layers Trainable Pooling method is a key contribution. It differs from previous trainable pooling methods (like NV-Embed, which uses only the last layer) by taking hidden states from *all* layers and processing them with a cross-attention network that includes a trainable layer weight matrix and a trainable query matrix. The paper provides evidence (Figure 1 and 2) that different layers encode distinct and potentially useful information.

While the paper shows that Multi-Layers Trainable Pooling (especially with bidirectional attention) performs well on STS and Retrieval tasks, it doesn't fully ablate the components of this *new* pooling method itself. Specifically, two important aspects are not thoroughly investigated:

1.  **Which layers are most important for the Multi-Layers Trainable Pooling?** The method uses *all* layers. Figure 2 suggests that intermediate layers can be better than the last layer *before* fine-tuning. An ablation is needed to see if using all layers is truly optimal *after* fine-tuning, or if a subset (e.g., top K layers, or a specific range) would be more effective or efficient. This directly tests the core hypothesis behind the multi-layer approach.
2.  **Is the trainable layer weight matrix necessary?** The proposed method introduces a trainable layer weight matrix (W) combined with the hidden states before the cross-attention. Ablating this component would reveal its contribution to the performance of the Multi-Layers Trainable Pooling method.

These two missing ablations are crucial for understanding the effectiveness of the proposed Multi-Layers Trainable Pooling strategy and providing guidance on its optimal design. They directly address components unique to the novel method introduced in the paper.

The metrics to report should align with those used in the paper: STS (Spearman), Retrieval (NDCG@10), Classification (Accuracy), and Clustering (V-measure), along with statistical significance testing where applicable.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Multi-Layers Pooling Layer Selection
- **Ablated Part**: The set of hidden layers used as input to the Multi-Layers Trainable Pooling network.
- **Action**: REPLACE
- **Replacement**: 
  - Top 4 layers
  - Top 8 layers
  - Top 16 layers
  - All layers (current method)
- **Metrics**: STS, Clas., Retr., Clus.

### Multi-Layers Pooling Trainable Layer Weights
- **Ablated Part**: The trainable layer weight matrix (W) in the Multi-Layers Trainable Pooling method.
- **Action**: REMOVE
- **Metrics**: STS, Clas., Retr., Clus.

</div>