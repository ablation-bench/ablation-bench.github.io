<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Machine_Learning_from_Explanations

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Machine Learning from Explanations" proposes a novel two-stage training pipeline to leverage explanations (subsets of influential input features) for training models on small datasets. The method consists of a feature extractor `f`, a mapping layer `m`, and a classifier `c`. The training alternates between two stages:
1.  Optimizing the standard label loss (cross-entropy) by updating the entire model (`f`, `m`, `c`).
2.  Optimizing a feature misalignment loss (`KL(softmax(f(x')) || softmax(m(f(x))))`) between the feature map of the masked input (`x'` derived from the explanation `e(x)`) and the feature map passed to the classifier. This stage *only* updates the mapping layer `m`.

The paper includes an ablation study (Section C) comparing their full method ("Ours") against two variants:
*   "No Mapping Layer": The feature misalignment loss updates the feature extractor `f` instead of a dedicated mapping layer `m`.
*   "Joint Opt": The label loss and feature misalignment loss are optimized jointly via gradient descent, similar to prior work but using the proposed feature misalignment loss and mapping layer.

This existing ablation study effectively demonstrates the importance of both the two-stage optimization structure and the introduction of the mapping layer `m` for updating based on the feature misalignment loss.

However, the existing ablations do not explore the specific choices made within the second stage's objective function or its optimization. Two key aspects of the second stage that are not ablated are:

1.  **The formulation of the feature misalignment loss:** The paper uses KL divergence between softmax-normalized feature maps. While justified intuitively, it's not compared against alternative loss functions (e.g., L2 distance) or different normalization schemes (e.g., L1, L2, or no normalization). Ablating this would show whether the specific choice of KL divergence and softmax is critical to the method's success.
2.  **The relative learning rates of the two stages:** The two stages use potentially different learning rates (η1 for label loss, η2 for feature misalignment loss). The paper mentions tuning these and adapting η2 in certain scenarios, implying their balance is important. A systematic ablation of the ratio between η1 and η2 would reveal the sensitivity of the method to the weighting of the two optimization objectives.

Based on their importance to the core mechanism of the second stage, I propose the following two missing ablation studies, ranked by their perceived impact on understanding the method's core technical contributions. Ablating the loss function formulation is slightly more fundamental than ablating the learning rate balance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablate Feature Misalignment Loss
- **Ablated Part**: Formulation of the feature misalignment loss (KL divergence between softmax-normalized feature maps)
- **Action**: REPLACE
- **Replacement**: 
  - L2 distance between raw feature maps
  - L2 distance between L2-normalized feature maps
- **Metrics**: Test Accuracy, Consistency (Pairwise Agreement)

### Ablate Learning Rate Ratio
- **Ablated Part**: Relative learning rates (η1 and η2) for the two optimization stages
- **Action**: REPLACE
- **Replacement**: 
  - η2 = 0.1 * η1
  - η2 = η1
  - η2 = 10 * η1
- **Metrics**: Test Accuracy, Consistency (Pairwise Agreement)

</div>