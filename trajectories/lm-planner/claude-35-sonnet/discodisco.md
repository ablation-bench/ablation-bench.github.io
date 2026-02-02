<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/discodisco

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, DisCoDisCo is a Transformer-based system that combines contextualized word embeddings (CWEs) with hand-crafted features for three tasks: discourse segmentation, connective detection, and relation classification. Here's my reasoning for the suggested ablations:

1. The most critical ablation would be testing the impact of hand-crafted features, as this is one of the main contributions claimed by the authors. They mention that while Transformers are powerful, some textual features are difficult for them to capture.

2. The choice of pre-trained models is crucial, especially for relation classification where they claim models pre-trained with Next Sentence Prediction (NSP) are optimal. This deserves verification.

3. For relation classification, they use a unique approach with pseudo-tokens for direction marking ('{', '}', '<', '>'). This novel technique should be evaluated.

4. The system uses multiple types of embeddings (character, fastText, and contextual). Testing their individual contributions would be valuable.

5. For connective detection specifically, they use CRF-based sequence tagging while using simple linear projection for segmentation. This architectural choice should be validated.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Feature Ablation
- **Ablated Part**: hand-crafted features
- **Action**: REMOVE
- **Metrics**: F1, Precision, Recall

### NSP Model Comparison
- **Ablated Part**: pre-trained model selection
- **Action**: REPLACE
- **Replacement**: 
  - bert-base-uncased
  - roberta-base
  - xlm-roberta-base
- **Metrics**: F1, Precision, Recall

### Direction Marking
- **Ablated Part**: direction pseudo-tokens in relation classification
- **Action**: REMOVE
- **Metrics**: F1, Precision, Recall

### Embedding Types
- **Ablated Part**: embedding combination
- **Action**: REPLACE
- **Replacement**: 
  - only-contextual
  - only-fastText
  - only-char
- **Metrics**: F1, Precision, Recall

### Sequence Decoder
- **Ablated Part**: CRF layer in connective detection
- **Action**: REPLACE
- **Replacement**: 
  - linear-projection
  - softmax
- **Metrics**: F1, Precision, Recall

</div>