<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/discodisco

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The following five ablation studies target the key components of DisCoDisCo that the paper argues contribute to its strong performance. The first and most important experiment removes the integrated hand‐crafted features from the segmentation and connective detection module to evaluate their overall benefit beyond the contextualized embeddings. Next, we focus on the relation classification module. One ablation removes the additional feature vector (inserted between the [CLS] token and unit tokens) which integrates hand-crafted relation features. Another ablation removes the pseudo-token markers that encode discourse relation direction, testing whether representing direction explicitly is helpful. In a fourth study, we replace the NSP-pretrained language model used in relation classification with alternatives that lack NSP pretraining (e.g. RoBERTa or XLNet) to assess the impact of this pretraining signal. Finally, we remove the neighbor sentence context (encoded via a bi-LSTM over preceding/following sentences) from the segmentation module. These targeted studies will help quantify the contribution of each component using metrics (such as F1 and Accuracy) that are standard and reported in the paper.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Remove Hand-Crafted Features in Segmentation & Connective Detection
- **Ablated Part**: The integration of hand-crafted categorical and numerical features (e.g., UD tags, sentence type, POS) that supplement contextualized word embeddings
- **Action**: REMOVE
- **Metrics**: F1

### Ablation 2: Remove Relation-Specific Additional Feature Vector
- **Ablated Part**: The extra feature vector inserted between the [CLS] token and the first token of unit 1 in the relation classification module that encodes document-level and pair-level hand-crafted features
- **Action**: REMOVE
- **Metrics**: F1, Accuracy

### Ablation 3: Remove Direction Pseudo-Tokens in Relation Classification
- **Ablated Part**: The pseudo-token markers (e.g., '}', '>', '{', '<') inserted to encode the directionality of discourse relations
- **Action**: REMOVE
- **Metrics**: F1, Accuracy

### Ablation 4: Replace NSP-Pretrained Language Model in Relation Classification
- **Ablated Part**: The choice of pretrained Transformer model for relation classification emphasizing NSP pretraining
- **Action**: REPLACE
- **Replacement**: 
  - roberta-base
  - xlnet-base-cased
- **Metrics**: F1, Accuracy

### Ablation 5: Remove Neighbor Sentence Context in Segmentation
- **Ablated Part**: The bi-LSTM based neighbor sentence embeddings that summarize preceding and following sentence context and are concatenated to every word representation
- **Action**: REMOVE
- **Metrics**: F1

</div>