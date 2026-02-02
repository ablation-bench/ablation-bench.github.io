<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/simcse

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The SimCSE paper introduces a simple yet effective contrastive learning framework for sentence embeddings, leveraging both unsupervised and supervised approaches. The key components of the method include the use of dropout as a minimal data augmentation technique, the incorporation of natural language inference (NLI) datasets for supervised learning, and the contrastive learning objective that regularizes the embedding space. To understand the contribution of each component to the overall performance, I suggest the following ablation studies:

1. **Dropout as Data Augmentation**: The paper highlights the importance of dropout in preventing representation collapse. An ablation study could involve removing dropout to observe its impact on the model's performance.

2. **Temperature Parameter in Contrastive Loss**: The temperature parameter in the contrastive loss function affects the separation of positive and negative pairs. Testing different values can provide insights into its role in the learning process.

3. **Use of NLI Datasets**: The supervised approach uses entailment pairs from NLI datasets as positives and contradiction pairs as hard negatives. Ablating the use of contradiction pairs can help understand their contribution to the model's performance.

4. **Pooling Methods**: The paper mentions different pooling methods (e.g., CLS token with MLP, first-last average). Ablating these methods can reveal their impact on the final sentence embeddings.

5. **Hard Negatives in Supervised Learning**: The use of contradiction pairs as hard negatives is a novel aspect of the supervised approach. An ablation study could involve removing these hard negatives to assess their importance.

These ablation studies will help attribute the performance improvements to specific components of the SimCSE framework and provide a deeper understanding of the method's effectiveness.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Dropout as data augmentation
- **Action**: REMOVE
- **Metrics**: Spearman's correlation, alignment, uniformity

### Ablation 2
- **Ablated Part**: Temperature parameter in contrastive loss
- **Action**: REPLACE
- **Replacement**: 
  - 0.01
  - 0.05
  - 0.1
  - 0.5
- **Metrics**: Spearman's correlation

### Ablation 3
- **Ablated Part**: Use of contradiction pairs as hard negatives
- **Action**: REMOVE
- **Metrics**: Spearman's correlation

### Ablation 4
- **Ablated Part**: Pooling methods
- **Action**: REPLACE
- **Replacement**: 
  - CLS with MLP
  - first-last average
- **Metrics**: Spearman's correlation

### Ablation 5
- **Ablated Part**: Hard negatives in supervised learning
- **Action**: REMOVE
- **Metrics**: Spearman's correlation

</div>