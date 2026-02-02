<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/seg-uncertainty

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The goal is to propose important ablation studies for the paper "Unsupervised Scene Adaptation with Memory Regularization in vivo". The paper introduces a method that uses the model's internal components (primary and auxiliary classifiers) as a "memory module" to enforce prediction consistency on unlabeled target data, termed memory regularization ($L_{mr}$). This is applied within a two-stage training framework that also includes standard domain adaptation techniques like adversarial loss and self-training with pseudo labels.

Based on the paper's description and its own ablation studies (Tables 1 and 2), the key components contributing to the performance are:
1.  The Memory Regularization loss ($L_{mr}$), which is the core novel contribution.
2.  The two-stage training process, where Stage-II involves self-training with pseudo labels.
3.  The use of both a primary and an auxiliary classifier, which enables the $L_{mr}$ calculation.
4.  The adversarial loss ($L_{adv}$) for inter-domain alignment (though the paper positions $L_{mr}$ as orthogonal).

The paper already shows the effect of $L_{mr}$ and $L_{adv}$ in Stage-I (Table 2). However, it does not explicitly show the performance of the full two-stage method when $L_{mr}$ is completely removed from both stages. It also doesn't quantify the contribution of Stage-II (self-training) by removing it entirely. Furthermore, the sensitivity to the weight of $L_{mr}$ ($\lambda_{mr}$) and the specific pseudo-labeling strategy used in Stage-II are not explored.

Therefore, the most important ablation studies to propose, ranked by their significance in validating the method's core claims and understanding its behavior, are:

1.  **Removing Memory Regularization ($L_{mr}$) entirely:** This directly tests the impact of the paper's main contribution on the final performance of the full two-stage method.
2.  **Removing Stage-II (Self-Training):** This evaluates the contribution of the pseudo-labeling based fine-tuning stage, which is a common technique but its interaction with $L_{mr}$ is part of the proposed method.
3.  **Varying the weight of $L_{mr}$ ($\lambda_{mr}$):** This hyperparameter study assesses the sensitivity of the method to the strength of the memory regularization.
4.  **Testing different Pseudo-labeling strategies:** This explores how the combination of primary and auxiliary classifier outputs for generating pseudo-labels in Stage-II affects performance.

These ablations cover the novelty ($L_{mr}$), the overall training structure (two stages), and key implementation details ($\lambda_{mr}$, pseudo-labeling). The primary metric used in the paper for evaluating performance is mean Intersection over Union (mIoU), which should be used for these ablations.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: No Memory Regularization
- **Ablated Part**: Memory Regularization loss (L_mr) in both Stage-I and Stage-II
- **Action**: REMOVE
- **Metrics**: mIoU

### Ablation: No Stage-II Self-Training
- **Ablated Part**: Stage-II training with pseudo labels and L_mr
- **Action**: REMOVE
- **Metrics**: mIoU

### Ablation: Vary Memory Regularization Weight
- **Ablated Part**: Weight of Memory Regularization loss (lambda_mr)
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.05
  - 0.1
  - 0.2
  - 0.5
- **Metrics**: mIoU

### Ablation: Pseudo-labeling Strategy
- **Ablated Part**: Combination strategy for pseudo-label generation in Stage-II
- **Action**: REPLACE
- **Replacement**: 
  - argmax(F_p)
  - argmax(F_a)
  - argmax(F_p + 0.5*F_a)
  - argmax(F_p + F_a)
- **Metrics**: mIoU

</div>