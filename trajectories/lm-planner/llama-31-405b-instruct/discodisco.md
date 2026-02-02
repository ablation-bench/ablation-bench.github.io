<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-31-405b-instruct/discodisco

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The DisCoDisCo system is a complex model that incorporates multiple components, including a sequence tagging model for segmentation and connective detection, and a BERT-based model for relation classification. To better understand the contributions of each component, I suggest the following ablation studies:

1. Remove the hand-crafted features from the sequence tagging model to see how much they contribute to the overall performance.
2. Replace the BERT-based model with a different pre-trained language model to see if the results are model-specific.
3. Remove the direction feature from the relation classification module to see if it has a significant impact on performance.
4. Add more features to the relation classification module to see if it improves performance.
5. Use a different optimizer or learning rate schedule to see if it affects the overall performance of the system.

These ablation studies will help to identify the most important components of the DisCoDisCo system and provide insights for future improvements.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: hand-crafted features
- **Action**: REMOVE
- **Metrics**: F1 score, accuracy

### Ablation 2
- **Ablated Part**: BERT-based model
- **Action**: REPLACE
- **Replacement**: 
  - RoBERTa
  - XLNet
- **Metrics**: F1 score, accuracy

### Ablation 3
- **Ablated Part**: direction feature
- **Action**: REMOVE
- **Metrics**: F1 score, accuracy

### Ablation 4
- **Ablated Part**: relation classification module
- **Action**: ADD
- **Replacement**: 
  - more features
- **Metrics**: F1 score, accuracy

### Ablation 5
- **Ablated Part**: optimizer
- **Action**: REPLACE
- **Replacement**: 
  - Adam
  - SGD
- **Metrics**: F1 score, accuracy

</div>