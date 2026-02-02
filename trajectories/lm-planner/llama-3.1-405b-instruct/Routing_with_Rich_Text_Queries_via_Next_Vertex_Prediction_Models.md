<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Routing_with_Rich_Text_Queries_via_Next_Vertex_Prediction_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents a novel approach to routing problems on graphs using autoregressive modeling via transformers. The authors propose a multimodal architecture that jointly encodes text and graph data and trains the architecture via next-token prediction. The paper demonstrates the effectiveness of this approach on synthetic graphs and real-world data from the OpenStreetMap repository.

Upon reviewing the paper, I noticed that the authors did not conduct ablation studies on two important aspects of their method: (1) the impact of the road embedding network on the overall performance, and (2) the effect of the secondary scoring model on the final route selection.

To address these gaps, I suggest two missing ablation studies:

1. **Ablating the road embedding network**: The authors could train a variant of their model without the road embedding network and instead use a simple embedding table to represent vertices and edges. This would help understand the contribution of the road embedding network to the overall performance.
2. **Ablating the secondary scoring model**: The authors could evaluate the performance of their model without the secondary scoring model and instead use a simple greedy decoding or beam search to select the final route. This would help understand the impact of the secondary scoring model on the final route selection.

These ablation studies would provide valuable insights into the importance of these components and help identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: road embedding network
- **Action**: REMOVE
- **Metrics**: Fulfills Query, Excess Travel Time, GT Route Recovery

### Ablation B
- **Ablated Part**: secondary scoring model
- **Action**: REMOVE
- **Metrics**: Fulfills Query, Excess Travel Time, GT Route Recovery

</div>