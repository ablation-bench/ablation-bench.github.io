<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/discodisco

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The DisCoDisCo system is a Transformer-based neural classifier that enhances contextualized word embeddings (CWEs) with hand-crafted features for discourse segmentation, connective detection, and relation classification. The system uses tokenwise sequence tagging for segmentation and connective detection, and a feature-rich, encoder-less sentence pair classifier for relation classification. The paper highlights the importance of features beyond CWEs and the effectiveness of models pre-trained on the Next Sentence Prediction (NSP) task for relation classification.

To design ablation studies, we should focus on the key components of the system: the use of hand-crafted features, the choice of pre-trained language models, and the specific architectural choices for each task. The goal is to understand the contribution of each component to the overall performance.

1. Hand-crafted features: The paper emphasizes the importance of hand-crafted features in addition to CWEs. An ablation study could involve removing these features to assess their impact on performance.

2. Pre-trained language models: The choice of pre-trained models, especially those trained on the NSP task, is highlighted as crucial for relation classification. An ablation study could involve replacing these models with others not trained on NSP to evaluate their impact.

3. Sequence tagging approach: The system uses a tokenwise classification approach for segmentation and a CRF-based sequence tagger for connective detection. An ablation study could involve replacing the CRF with a simpler linear projection layer to assess its necessity.

4. Feature-rich sentence pair classifier: The relation classification component uses a feature-rich, encoder-less classifier. An ablation study could involve removing the additional features to evaluate their contribution.

5. Directionality representation: The system uses pseudo-tokens to represent directionality in relation classification. An ablation study could involve removing these pseudo-tokens to assess their impact.

These ablation studies will help attribute the system's performance to its major components and provide insights into the importance of each component.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Hand-crafted features
- **Action**: REMOVE
- **Metrics**: F1, Accuracy

### Ablation 2
- **Ablated Part**: Pre-trained language models with NSP
- **Action**: REPLACE
- **Replacement**: 
  - BERT-base
  - RoBERTa-base
- **Metrics**: F1, Accuracy

### Ablation 3
- **Ablated Part**: CRF-based sequence tagger
- **Action**: REPLACE
- **Replacement**: 
  - Linear projection layer
- **Metrics**: F1, Accuracy

### Ablation 4
- **Ablated Part**: Feature-rich sentence pair classifier
- **Action**: REMOVE
- **Metrics**: F1, Accuracy

### Ablation 5
- **Ablated Part**: Directionality representation with pseudo-tokens
- **Action**: REMOVE
- **Metrics**: F1, Accuracy

</div>