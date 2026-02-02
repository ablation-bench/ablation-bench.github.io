<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/blockskim

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The Block-Skim method introduces a novel approach to improve the efficiency of Transformer models in extractive question answering tasks by skimming unnecessary context. The key components of this method include the use of self-attention weights to identify relevant context, a CNN-based block relevance predictor, and a joint training paradigm that optimizes both the QA task and block relevance prediction. To understand the contribution of each component to the overall performance, we can design several ablation studies.

1. **Self-Attention Weights for Relevance Prediction**: The method relies heavily on self-attention weights to determine the relevance of context blocks. An ablation study could involve removing this component to see how much it affects the model's ability to identify relevant context.

2. **CNN-based Block Relevance Predictor**: The CNN model processes attention heatmaps to predict block relevance. We could replace the CNN with simpler models or remove it entirely to assess its impact on performance.

3. **Joint Training Paradigm**: The joint training of the QA task and block relevance prediction is crucial for the model's performance. We could ablate this by training the components separately to see how joint training contributes to the final results.

4. **Diagonal Attention Simplification**: The simplification of attention heatmaps to only use diagonal regions is an optimization step. We could test the effect of using full attention maps versus diagonal maps on the model's efficiency and accuracy.

5. **Block Size Variation**: The choice of block size affects the granularity of the skimming process. We could experiment with different block sizes to determine the optimal configuration for balancing speed and accuracy.

These ablation studies will help isolate the effects of each component and provide insights into the most critical parts of the Block-Skim method.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Self-attention weights for relevance prediction
- **Action**: REMOVE
- **Metrics**: accuracy, F1 score, inference time

### Ablation 2
- **Ablated Part**: CNN-based block relevance predictor
- **Action**: REPLACE
- **Replacement**: 
  - linear model
  - decision tree
- **Metrics**: accuracy, F1 score, inference time

### Ablation 3
- **Ablated Part**: Joint training paradigm
- **Action**: REMOVE
- **Metrics**: accuracy, F1 score, inference time

### Ablation 4
- **Ablated Part**: Diagonal attention simplification
- **Action**: REPLACE
- **Replacement**: 
  - full attention map
- **Metrics**: accuracy, F1 score, inference time

### Ablation 5
- **Ablated Part**: Block size
- **Action**: REPLACE
- **Replacement**: 
  - 16
  - 64
  - 128
- **Metrics**: accuracy, F1 score, inference time

</div>