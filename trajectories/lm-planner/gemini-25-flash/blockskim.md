<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/blockskim

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Block-Skim: Efficient Question Answering for Transformer" proposes a method to accelerate Transformer inference for Question Answering by selectively processing only relevant parts of the input context. The core idea is to identify irrelevant blocks of tokens using a CNN-based predictor that analyzes attention weights from the Transformer layers. This predictor is trained jointly with the main QA task using a multi-objective loss function. Skimming (dropping irrelevant blocks) is applied during inference to reduce computation and achieve speedup. The paper claims improvements in both accuracy and speedup.

To understand the contribution of different components of the Block-Skim method, several ablation studies are crucial. Based on the paper's description, the key components are:
1.  The joint training objective, specifically the inclusion of the block-level relevance prediction loss.
2.  The CNN-based predictor itself and its input (attention weights, particularly the diagonal region).
3.  The block-level granularity of skimming.
4.  The inference-time skimming mechanism and the rate at which blocks are skimmed.

I will propose up to 5 ablation studies focusing on these aspects, ranked by their importance in validating the core claims and understanding the method's mechanics. The primary metrics used in the paper are QA accuracy (likely F1 and Exact Match for extractive QA) and inference speedup.

1.  **Varying Skimming Rate:** The most direct way to evaluate the method's effectiveness is to see the trade-off between speedup and accuracy by varying how aggressively blocks are skimmed during inference. This shows the practical utility of the learned relevance prediction.
2.  **Removing Block-Skim Loss:** The paper uses a joint training objective. Ablating the Block-Skim specific loss term allows us to see if the auxiliary task signal is necessary or beneficial for training the model, even if skimming is still applied at inference (or to see the performance of the model trained without this signal when skimming is applied).
3.  **Varying Loss Weights ($\alpha, \beta$):** The joint loss uses hyperparameters $\alpha$ and $\beta$ to balance the QA loss and the Block-Skim loss. Investigating different values for these weights helps understand the sensitivity of the training process to this balance.
4.  **CNN Predictor Input:** The paper justifies using only the diagonal attention region as input to the CNN predictor for efficiency. Comparing performance when using the full attention map as input would validate this design choice.
5.  **Varying Block Size:** The method operates on blocks of tokens. The choice of block size ($k$) is a hyperparameter that likely affects both the granularity of skimming and the potential speedup. Ablating this parameter would show its impact.

These five ablations cover the training objective, the predictor design, the inference strategy, and a key structural parameter, providing a comprehensive evaluation of the Block-Skim method.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation_SkimmingRate
- **Ablated Part**: Skimming rate/threshold during inference
- **Action**: REPLACE
- **Replacement**: 
  - lower skimming rate
  - higher skimming rate
  - no skimming (baseline)
- **Metrics**: F1, Exact Match, Speedup

### Ablation_RemoveBlockSkimLoss
- **Ablated Part**: Block-Skim loss term in the joint training objective
- **Action**: REMOVE
- **Metrics**: F1, Exact Match, Speedup

### Ablation_VaryLossWeights
- **Ablated Part**: Hyperparameters alpha and beta in the joint training loss
- **Action**: REPLACE
- **Replacement**: 
  - different values for alpha and beta
- **Metrics**: F1, Exact Match, Speedup

### Ablation_CNNInput
- **Ablated Part**: Input to the CNN predictor
- **Action**: REPLACE
- **Replacement**: 
  - full attention map
  - diagonal attention map
- **Metrics**: F1, Exact Match, Speedup

### Ablation_BlockSize
- **Ablated Part**: Block size k
- **Action**: REPLACE
- **Replacement**: 
  - smaller block size
  - larger block size
- **Metrics**: F1, Exact Match, Speedup

</div>