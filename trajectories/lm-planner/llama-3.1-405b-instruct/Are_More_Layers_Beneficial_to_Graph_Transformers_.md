<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Are_More_Layers_Beneficial_to_Graph_Transformers_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Are More Layers Beneficial to Graph Transformers?" explores the effectiveness of increasing the depth of graph transformers. The authors find that current graph transformers suffer from a bottleneck in improving performance by increasing depth, which is attributed to the vanishing capacity of global attention. To address this issue, they propose a novel graph transformer model named DeepGraph that employs substructure tokens in the encoded representation and applies local attention on related nodes to obtain substructure-based attention encoding.

The authors conduct experiments on various graph benchmarks and demonstrate that their method unblocks the depth limitation of graph transformers and achieves state-of-the-art performance. They also provide theoretical results to support their claims, including the definition of attention capacity and its variation with depth.

To further investigate the effectiveness of DeepGraph, we suggest two missing ablation studies:

1. **Ablation study on the impact of substructure token encoding**: This study would involve removing the substructure token encoding component from DeepGraph and evaluating the model's performance. This would help to understand the contribution of substructure token encoding to the overall performance of the model.
2. **Ablation study on the effect of local attention on substructures**: In this study, the local attention mechanism on substructures would be replaced with a global attention mechanism, and the model's performance would be evaluated. This would help to understand the importance of local attention on substructures in DeepGraph.

These ablation studies would provide further insights into the effectiveness of the proposed components in DeepGraph and help to identify areas for potential improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: substructure token encoding
- **Action**: REMOVE
- **Metrics**: accuracy, F1 score

### Ablation Study 2
- **Ablated Part**: local attention on substructures
- **Action**: REPLACE
- **Replacement**: 
  - global attention
- **Metrics**: accuracy, F1 score

</div>