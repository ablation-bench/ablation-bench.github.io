<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/amrbart

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

To design ablation studies for the research titled "Graph Pre-training for AMR Parsing and Generation," we need to identify the key components of the method and investigate their impact on the overall performance. The method in question involves pre-training a BART model on AMR graphs and text data using two graph auto-encoding strategies and four tasks to integrate text and graph information during pre-training.

The first ablation study should investigate the impact of pre-training on AMR graphs. This can be done by comparing the performance of the model with and without pre-training on AMR graphs.

The second ablation study should examine the effect of the two graph auto-encoding strategies. This can be done by comparing the performance of the model using each strategy separately and both strategies together.

The third ablation study should investigate the impact of the four tasks used to integrate text and graph information during pre-training. This can be done by comparing the performance of the model using each task separately and all tasks together.

The fourth ablation study should examine the effect of the dynamic masking rate used in the pre-training tasks. This can be done by comparing the performance of the model using a static masking rate and a dynamic masking rate.

The fifth ablation study should investigate the impact of the unified pre-training framework. This can be done by comparing the performance of the model using the unified framework and a separate pre-training framework for each task.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: pre-training on AMR graphs
- **Action**: REMOVE
- **Metrics**: BLEU, METEOR, CHRF++

### Ablation 2
- **Ablated Part**: graph auto-encoding strategies
- **Action**: REPLACE
- **Replacement**: 
  - node/edge level denoising
  - sub-graph level denoising
  - both
- **Metrics**: BLEU, METEOR, CHRF++

### Ablation 3
- **Ablated Part**: tasks to integrate text and graph information
- **Action**: REPLACE
- **Replacement**: 
  - graph augmented text denoising
  - text augmented graph denoising
  - noisy graph augmented text denoising
  - noisy text augmented graph denoising
  - all
- **Metrics**: BLEU, METEOR, CHRF++

### Ablation 4
- **Ablated Part**: dynamic masking rate
- **Action**: REPLACE
- **Replacement**: 
  - static masking rate
  - dynamic masking rate
- **Metrics**: BLEU, METEOR, CHRF++

### Ablation 5
- **Ablated Part**: unified pre-training framework
- **Action**: REPLACE
- **Replacement**: 
  - separate pre-training framework
  - unified pre-training framework
- **Metrics**: BLEU, METEOR, CHRF++

</div>