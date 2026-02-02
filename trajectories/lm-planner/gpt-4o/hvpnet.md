<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/hvpnet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces a novel Hierarchical Visual Prefix fusion Network (HVPNeT) for multimodal named entity recognition (MNER) and relation extraction (MRE). The key components of the method include the use of visual prefixes to guide textual representation, a dynamic gated aggregation strategy for hierarchical multi-scaled visual features, and a visual prefix-guided fusion mechanism. The ablation studies should focus on these components to understand their contribution to the overall performance.

1. **Visual Prefix as a Pluggable Component**: The visual prefix is a central part of the method, acting as a guide for textual representation. An ablation study could involve removing the visual prefix to see how much it contributes to the model's performance.

2. **Dynamic Gated Aggregation Strategy**: This strategy is used to achieve hierarchical multi-scaled visual features. An ablation study could replace this strategy with a simpler aggregation method to evaluate its effectiveness.

3. **Hierarchical Multi-Scaled Visual Features**: The use of hierarchical features is inspired by practices in computer vision. An ablation study could involve using only global or only local features to assess the importance of hierarchical features.

4. **Visual Prefix-Guided Fusion Mechanism**: This mechanism integrates visual features into each self-attention layer of BERT. An ablation study could involve replacing this mechanism with a simpler concatenation or attention mechanism to evaluate its impact.

5. **Dynamic Gate Module**: The dynamic gate module predicts path probabilities for visual features. An ablation study could involve removing the dynamic gate to see how it affects the model's ability to leverage visual features.

The metrics to report should include those used in the paper, such as accuracy, F1 score, and any other relevant metrics for MNER and MRE tasks.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Visual Prefix
- **Action**: REMOVE
- **Metrics**: accuracy, F1 score

### Ablation 2
- **Ablated Part**: Dynamic Gated Aggregation Strategy
- **Action**: REPLACE
- **Replacement**: 
  - simple average pooling
  - max pooling
- **Metrics**: accuracy, F1 score

### Ablation 3
- **Ablated Part**: Hierarchical Multi-Scaled Visual Features
- **Action**: REPLACE
- **Replacement**: 
  - only global features
  - only local features
- **Metrics**: accuracy, F1 score

### Ablation 4
- **Ablated Part**: Visual Prefix-Guided Fusion Mechanism
- **Action**: REPLACE
- **Replacement**: 
  - simple concatenation
  - standard attention
- **Metrics**: accuracy, F1 score

### Ablation 5
- **Ablated Part**: Dynamic Gate Module
- **Action**: REMOVE
- **Metrics**: accuracy, F1 score

</div>