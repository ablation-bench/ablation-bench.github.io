<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Are_More_Layers_Beneficial_to_Graph_Transformers_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Are More Layers Beneficial to Graph Transformers?" proposes DeepGraph, a novel graph transformer model designed to overcome the depth limitation of existing models. The core ideas are the introduction of explicit substructure tokens and the application of local attention based on these tokens, combined with techniques like deepnorm and relative position encoding.

The paper includes several ablation and sensitivity studies to validate the effectiveness of different components:
1.  **Ablation of Local Attention:** Demonstrates the importance of the substructure-based local attention mechanism.
2.  **Ablation of Substructure Encoding:** Shows the benefit of learning substructure representations compared to random initialization.
3.  **Ablation of Deepnorm:** Confirms the role of deepnorm in stabilizing training for deeper models.
4.  **Sensitivity to Substructure Types:** Evaluates the impact of using geometric vs. neighbor substructures.
5.  **Sensitivity to Neighbor Size:** Checks robustness to the size parameter for neighbor substructures.

While these ablations cover key aspects like local attention, the existence of substructure tokens, and training stability, they do not fully explore the specific *methods* used for generating and selecting these substructure tokens. Two potentially important missing ablations relate to:

1.  **Substructure Token Encoding:** The paper uses a specific permutation-based encoding method (DFS with degree sorting) for substructure tokens. It's important to understand if this particular encoding method is crucial for performance, or if a simpler approach to representing the substructure (e.g., pooling node features within the substructure) would suffice. Ablating this would isolate the contribution of their chosen encoding scheme.
2.  **Substructure Sampling Strategy:** The paper employs a greedy, coverage-based sampling algorithm for substructures. Evaluating a simpler sampling strategy (like purely random sampling) would reveal whether their sophisticated sampling method significantly contributes to performance or primarily serves computational efficiency or coverage goals. This is particularly relevant for the scalability and general applicability of the method.

These two ablations are important because they investigate specific technical implementations within the DeepGraph framework that are not currently isolated in the paper's experimental evaluation. Understanding their individual impact is key to fully appreciating the contributions of the proposed method. I will prioritize the encoding method ablation as it directly impacts the representation quality of the substructure tokens, which are central to the model.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Substructure Token Encoding
- **Ablated Part**: Permutation-based encoding method for substructure tokens
- **Action**: REPLACE
- **Replacement**: 
  - Mean Pooling of node features
  - Sum Pooling of node features
  - Max Pooling of node features
- **Metrics**: ZINC ↓, CLUSTER ↑

### Ablation: Substructure Sampling Strategy
- **Ablated Part**: Greedy, coverage-based substructure sampling algorithm
- **Action**: REPLACE
- **Replacement**: 
  - Random Sampling
- **Metrics**: ZINC ↓, CLUSTER ↑

</div>