<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-31-405b-instruct/blockskim

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

To design ablation studies for the Block-Skim research, we need to identify the key components of the method and then propose experiments to isolate their effects. The Block-Skim method involves using a CNN-based model to predict the relevance of blocks of tokens in a context paragraph for question answering. The key components include the use of attention weights from the Transformer model, the CNN architecture for block relevance prediction, and the joint training objective that combines the QA loss and the block-level relevance classification loss.

The first ablation study (Ablation A) should investigate the impact of using attention weights for block relevance prediction. This can be done by comparing the performance of the Block-Skim model with a variant that uses a different feature for prediction, such as the hidden states of the Transformer model.

The second ablation study (Ablation B) should examine the effect of the CNN architecture on the block relevance prediction accuracy. This can be done by comparing the performance of the Block-Skim model with a variant that uses a different architecture, such as a fully connected neural network.

The third ablation study (Ablation C) should investigate the impact of the joint training objective on the QA accuracy and the block-level relevance classification accuracy. This can be done by comparing the performance of the Block-Skim model with a variant that trains the QA and block-level relevance classification objectives separately.

The fourth ablation study (Ablation D) should examine the effect of the block size on the performance of the Block-Skim model. This can be done by comparing the performance of the Block-Skim model with different block sizes.

The fifth ablation study (Ablation E) should investigate the impact of the harmony coefficient and the balance factor on the performance of the Block-Skim model. This can be done by comparing the performance of the Block-Skim model with different values of these hyperparameters.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: attention weights
- **Action**: REPLACE
- **Replacement**: 
  - hidden states
- **Metrics**: accuracy, F1 score

### Ablation B
- **Ablated Part**: CNN architecture
- **Action**: REPLACE
- **Replacement**: 
  - fully connected neural network
- **Metrics**: accuracy, F1 score

### Ablation C
- **Ablated Part**: joint training objective
- **Action**: REMOVE
- **Metrics**: accuracy, F1 score

### Ablation D
- **Ablated Part**: block size
- **Action**: REPLACE
- **Replacement**: 
  - 16
  - 32
  - 64
- **Metrics**: accuracy, F1 score

### Ablation E
- **Ablated Part**: harmony coefficient and balance factor
- **Action**: REPLACE
- **Replacement**: 
  - [0.1, 0.5]
  - [0.5, 0.1]
- **Metrics**: accuracy, F1 score

</div>