<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Routing_with_Rich_Text_Queries_via_Next_Vertex_Prediction_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a novel approach to customized routing using a multimodal transformer model trained via next-vertex prediction, conditioned on rich text queries and graph data. The core components include a multimodal architecture (text encoder, road embedding network for graph data, base transformer network), a next-vertex prediction training objective, and inference algorithms (beam search, optionally with a secondary scoring model).

The paper includes several ablation studies in Appendix B:
1.  **Receptive Field (B.1):** Investigates the size of the k-hop neighborhood used for road features.
2.  **Scaling Studies (B.2):** Examines the impact of scaling the base network and the road embedding network depth.
3.  **Road Embedding Network Architecture (B.5):** Compares using transformers vs. only MLPs within the road embedding network for processing sequence features.
4.  **Secondary Scoring Model (B.9):** Evaluates the contribution of the learned secondary model used during inference.
5.  **Inference Algorithms (B.10):** Compares different decoding strategies (Greedy, Beam Search, Dijkstra-like).

Based on the method description and existing ablations, I identify two important missing ablation studies that would further clarify the contribution of key components:

1.  **Ablating the Text Query:** The paper's main contribution is handling "rich text queries". An essential ablation is to remove the text query input entirely. This would demonstrate the performance degradation when the model cannot condition its predictions on the user's specific requests, quantifying the value of the text encoding and multimodal fusion with the query. The model would effectively become a path prediction model conditioned only on source, destination, and path history.
2.  **Ablating Complex Road Features:** The paper introduces a sophisticated "Road Embedding Network" that processes sequences of vectors encoding k-hop neighborhood information. While B.5 ablates the *architecture* of this network (Transformer vs MLP on sequence/flattened features), it doesn't directly ablate the *complexity* of the features themselves. A valuable ablation would be to replace these complex k-hop neighborhood features with simpler, fixed-size features derived from basic node/edge attributes (e.g., type, coordinates, degree, POI presence flags) and process these simpler features with a basic MLP. This would assess whether the performance gains are due to the complex neighborhood features or simply having some form of learned graph embedding.

These two ablations are crucial because they directly test the contribution of the two main novel inputs: the rich text query and the complex graph feature representation designed for scalability and generalization. They are ranked by importance, with the text query ablation being slightly more central to the paper's title and core problem statement. The metrics used should align with those reported in the paper's main results (Tables 1, 2, 3): Fulfills Query, Excess Travel Time, and GT Route Recovery.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablating Text Query
- **Ablated Part**: Text query input to the model
- **Action**: REMOVE
- **Metrics**: Fulfills Query, Excess Travel Time, GT Route Recovery

### Ablating Complex Road Features
- **Ablated Part**: K-hop neighborhood sequence features used in the Road Embedding Network
- **Action**: REPLACE
- **Replacement**: 
  - Basic node/edge attributes (e.g., type, coordinates, degree, POI presence flags) as fixed-size features processed by a simple MLP
- **Metrics**: Fulfills Query, Excess Travel Time, GT Route Recovery

</div>