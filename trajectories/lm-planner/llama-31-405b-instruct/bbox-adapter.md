<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-31-405b-instruct/bbox-adapter

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

To design ablation studies for the BBox-Adapter, we need to identify the key components of the method and analyze their impact on the overall performance. The BBox-Adapter is a lightweight adapter for black-box large language models (LLMs) that uses a ranking-based noise contrastive estimation (NCE) loss to promote the likelihood of target domain data while penalizing that of the source domain.

The first ablation study we suggest is to remove the ranking-based NCE loss and replace it with a standard NCE loss. This will help us understand the importance of the ranking-based approach in the BBox-Adapter.

The second ablation study is to remove the online adaptation mechanism and use a fixed set of positive and negative samples for training. This will help us understand the impact of the online adaptation mechanism on the performance of the BBox-Adapter.

The third ablation study is to change the size of the adapter model and analyze its impact on the performance. This will help us understand the trade-off between model size and performance.

The fourth ablation study is to use different types of feedback (e.g., human feedback, AI feedback) and analyze their impact on the performance of the BBox-Adapter.

The fifth ablation study is to apply the BBox-Adapter to different LLMs and analyze its impact on the performance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: ranking-based NCE loss
- **Action**: REPLACE
- **Replacement**: 
  - standard NCE loss
- **Metrics**: accuracy, F1 score

### Ablation 2
- **Ablated Part**: online adaptation mechanism
- **Action**: REMOVE
- **Metrics**: accuracy, F1 score

### Ablation 3
- **Ablated Part**: adapter model size
- **Action**: REPLACE
- **Replacement**: 
  - small
  - medium
  - large
- **Metrics**: accuracy, F1 score

### Ablation 4
- **Ablated Part**: feedback type
- **Action**: REPLACE
- **Replacement**: 
  - human feedback
  - AI feedback
- **Metrics**: accuracy, F1 score

### Ablation 5
- **Ablated Part**: LLM type
- **Action**: REPLACE
- **Replacement**: 
  - gpt-3.5-turbo
  - davinci-002
  - Mixtral-8x7B
- **Metrics**: accuracy, F1 score

</div>