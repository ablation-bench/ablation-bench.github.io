<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Routing_with_Rich_Text_Queries_via_Next_Vertex_Prediction_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Looking at the paper's method and experiments, I notice several key components that could benefit from ablation studies:

1. The paper already includes ablations for:
- Road embedding network architecture (comparing transformer vs MLP-only)
- Model scaling (embedding dimensions, network depth)
- Receptive field size for road features
- Points of interest density
- Secondary scoring model

However, I notice two critical missing ablations:

1. Query Encoding Method: The paper uses a standard transformer encoder for processing the natural language queries but doesn't ablate this component. Given that query understanding is crucial for the task, testing different query encoding architectures would be valuable.

2. Base Network Architecture: While the paper uses a decoder-only transformer architecture for the base network, it doesn't explore alternatives like encoder-decoder architectures which are common for sequence tasks. This is an important architectural choice that should be validated.

I'll prioritize these two ablations, with the query encoding being most important since query understanding is fundamental to the task.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Query Encoder Ablation
- **Ablated Part**: Query encoding architecture in the base network
- **Action**: REPLACE
- **Replacement**: 
  - BERT encoder
  - RNN encoder
  - Simple word embedding averaging
- **Metrics**: Fulfills Query, Excess Travel Time, GT Route Recovery

### Base Network Architecture Ablation
- **Ablated Part**: Decoder-only transformer architecture of the base network
- **Action**: REPLACE
- **Replacement**: 
  - Encoder-decoder transformer
  - RNN sequence-to-sequence model
- **Metrics**: Fulfills Query, Excess Travel Time, GT Route Recovery

</div>