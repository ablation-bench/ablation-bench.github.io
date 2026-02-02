<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/discodisco

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The DisCoDisCo system addresses three tasks: Discourse Unit Segmentation, Connective Detection, and Relation Classification. The system uses a Transformer-based approach enhanced with hand-crafted features. The segmentation and connective detection tasks are handled with a sequence tagging model, while relation classification uses a BERT-based sentence pair classifier.

Based on the paper's description, the key components contributing to the system's performance beyond the base Transformer models are:
1.  **Hand-crafted features:** Used in both the sequence tagging model (segmentation/connective detection) and the relation classification model. The paper mentions these were found to be helpful.
2.  **Neighboring sentence representation:** Used in the sequence tagging model to provide broader context.
3.  **Pseudo-tokens for direction:** Used in the relation classification model to encode the direction of the relation.
4.  **Choice of pretrained Transformer model:** Specifically, the paper notes that models pretrained on the Next Sentence Prediction (NSP) task were optimal for relation classification.

The paper mentions that ablation tests showed features beyond CWEs were helpful. However, it doesn't detail the specific impact of different feature sets or other architectural choices like the neighboring sentence representation or the pseudo-tokens. Quantifying the contribution of these specific enhancements is crucial. Additionally, confirming the impact of the NSP pretraining objective for relation classification through a direct comparison is valuable.

Therefore, I propose the following ablation studies, ranked by importance:

1.  **Ablate Hand-crafted Features (Relation Classification):** The paper highlights the use of hand-crafted features as a key enhancement. Ablating the entire set of these features for the relation classification task will directly measure their overall contribution to performance on this task.
2.  **Ablate Direction Pseudo-tokens (Relation Classification):** The paper explicitly states that the pseudo-tokens for encoding relation direction were helpful. This ablation quantifies the specific impact of this novel encoding method.
3.  **Ablate Neighbor Context (Segmentation/Connective Detection):** The sequence tagging model incorporates a representation of neighboring sentences. Ablating this component will show how much this explicit context contributes to segmentation and connective detection performance.
4.  **Ablate Static Embeddings (Segmentation/Connective Detection):** The sequence tagging model uses a concatenation of character, static (fastText), and contextualized embeddings. Ablating the static embeddings will reveal if they still provide unique value alongside the powerful contextualized embeddings.
5.  **Replace BERT (Non-NSP) (Relation Classification):** The paper found NSP-trained models optimal for relation classification. Replacing the chosen BERT model with a popular alternative not trained on NSP (like RoBERTa) will quantify the performance difference attributable to the pretraining objective.

The metrics chosen align with those reported in the paper for the respective tasks: F1 for segmentation and connective detection, and Macro F1 for relation classification.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablate Relation Features
- **Ablated Part**: Hand-crafted features added to the relation classification model
- **Action**: REMOVE
- **Metrics**: Macro F1

### Ablate Direction Pseudo-tokens
- **Ablated Part**: Pseudo-tokens used to encode relation direction in the relation classification model input
- **Action**: REMOVE
- **Metrics**: Macro F1

### Ablate Neighbor Context
- **Ablated Part**: Bi-LSTM encoded representation of preceding and following sentences in the segmentation/connective detection model
- **Action**: REMOVE
- **Metrics**: F1 (Segmentation), F1 (Connective Detection)

### Ablate Static Embeddings
- **Ablated Part**: fastText static word embeddings in the segmentation/connective detection model
- **Action**: REMOVE
- **Metrics**: F1 (Segmentation), F1 (Connective Detection)

### Replace BERT (Non-NSP)
- **Ablated Part**: Pretrained BERT model used for relation classification
- **Action**: REPLACE
- **Replacement**: 
  - roberta-base-cased
- **Metrics**: Macro F1

</div>