<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Rethinking_Multiple_Instance_Learning_From_Feature_Space_to_Probability_Space

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that the authors propose two main components in their PSMIL method:
1. Probability-space alignment (PSAli) - A self-training alignment strategy to handle feature drift
2. Probability-space attention pooling (PSAtt) - An alternative to traditional attention pooling

The paper already includes some ablation studies in Table 3, where they test:
- The impact of representation learning (RL)
- The effect of PSAli alone
- Different values of λT parameter for the alignment objective

However, I notice two important missing ablation studies:

1. The most critical missing ablation is testing different similarity estimation functions (Ψ) in the probability-space attention pooling component. Currently, they only use softmax(H^T Q) but don't explore alternatives. This is important since the similarity function directly affects how instance features are mapped to probability space.

2. Another important missing ablation is testing different momentum values (γ) for updating the class prototype matrix Q in equation 11. The paper uses a default value of 0.001 but doesn't justify this choice or explore its impact.

These ablations would help better understand the key design choices in the probability space components that are central to the method's performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Similarity Function Ablation
- **Ablated Part**: Similarity estimation function Ψ in probability-space attention pooling
- **Action**: REPLACE
- **Replacement**: 
  - cosine similarity
  - dot product
  - L2 distance
- **Metrics**: accuracy, AUC

### Momentum Value Ablation
- **Ablated Part**: Momentum parameter γ for updating class prototype matrix Q
- **Action**: REPLACE
- **Replacement**: 
  - 0.0001
  - 0.01
  - 0.1
- **Metrics**: accuracy, AUC

</div>