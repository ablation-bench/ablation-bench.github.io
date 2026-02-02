<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Routing_with_Rich_Text_Queries_via_Next_Vertex_Prediction_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two missing ablation studies that isolate two key multimodal components of the proposed system. First, while the paper compares performance on different query sources (template‐generated vs. LLM-generated), it does not explicitly remove the rich textual query input from the model. Evaluating a model that omits the text encoding branch will reveal the importance of the natural language query in guiding the route prediction. Second, the autoregressive next-vertex prediction is conditioned not only on the query but also on the prefix of the ground-truth route. Ablating (or removing) the route prefix input from the model input, so that only the source and destination (plus the query) are provided, will help quantify the role of route history in predicting the next vertex. Both ablations are expected to impact all primary metrics—namely, Query Fulfillment, Excess Travel Time, and Ground-Truth Route Recovery—as reported throughout the paper.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Text Query
- **Ablated Part**: The text query encoding module that processes the rich natural language query and integrates its semantics into the routing decision
- **Action**: REMOVE
- **Metrics**: Fulfills Query, Excess Travel Time, GT Route Recovery

### Ablation: Remove Route Prefix Context
- **Ablated Part**: The incorporation of the route prefix (the previously traversed vertices) in the next-vertex prediction, which provides context for incremental route unrolling
- **Action**: REMOVE
- **Metrics**: Fulfills Query, Excess Travel Time, GT Route Recovery

</div>