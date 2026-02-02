<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/cet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

To design ablation studies for the research titled "Preserving Commonsense Knowledge from Pre-trained Language Models via Causal Inference," we need to identify the key components of the proposed method, Causal Effect Tuning (CET), and analyze their impact on the model's performance. Here are five ablation study suggestions, ranked by their importance:

1. **Ablation of the causal objective**: Remove the causal objective from the overall objective function and fine-tune the model using only the vanilla fine-tuning objective. This ablation study will help us understand the contribution of the causal objective in preserving commonsense knowledge.

2. **Ablation of the KNN-based colliding effect estimation**: Replace the KNN-based colliding effect estimation with a random or uniform estimation method. This ablation study will help us understand the importance of using KNNs to estimate the colliding effect.

3. **Ablation of the similarity threshold**: Remove the similarity threshold (θ) and use a fixed number of nearest neighbors for all samples. This ablation study will help us understand the impact of the similarity threshold on the model's performance.

4. **Ablation of the weight controlling the strength of colliding effects (W0)**: Set W0 to 0 or 1 and analyze the impact on the model's performance. This ablation study will help us understand the importance of controlling the strength of colliding effects.

5. **Ablation of the heuristic approximation for estimating the causal effect on commonsense QA**: Replace the heuristic approximation with a different method, such as using the euclidean distance or cosine similarity between the average last hidden states of PLMs. This ablation study will help us understand the effectiveness of the proposed heuristic approximation.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Causal Objective
- **Ablated Part**: causal objective
- **Action**: REMOVE
- **Metrics**: accuracy, F1-score

### Ablation of KNN-based Colliding Effect Estimation
- **Ablated Part**: KNN-based colliding effect estimation
- **Action**: REPLACE
- **Replacement**: 
  - random estimation
  - uniform estimation
- **Metrics**: accuracy, F1-score

### Ablation of Similarity Threshold
- **Ablated Part**: similarity threshold
- **Action**: REMOVE
- **Metrics**: accuracy, F1-score

### Ablation of Weight Controlling Colliding Effects
- **Ablated Part**: weight controlling colliding effects (W0)
- **Action**: REPLACE
- **Replacement**: 
  - 0
  - 1
- **Metrics**: accuracy, F1-score

### Ablation of Heuristic Approximation for Commonsense QA
- **Ablated Part**: heuristic approximation for estimating causal effect on commonsense QA
- **Action**: REPLACE
- **Replacement**: 
  - euclidean distance
  - cosine similarity
- **Metrics**: accuracy, F1-score

</div>