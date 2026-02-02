<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/lbcs

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Refined Coreset Selection: Towards Minimal Coreset Size under Model Performance Constraints" introduces the problem of Refined Coreset Selection (RCS), which aims to find the smallest coreset size while maintaining model performance comparable to training on the full dataset. The proposed method, Lexicographic Bilevel Coreset Selection (LBCS), addresses this by formulating it as a bilevel optimization problem with lexicographic preferences, prioritizing model performance ($f_1$) over coreset size ($f_2$). The outer loop optimizes the coreset mask using a black-box randomized search guided by these lexicographic relations, and the inner loop trains the model on the selected coreset. A key aspect is the introduction of a voluntary performance compromise parameter $\epsilon$ for the primary objective $f_1$.

Based on this analysis, the most critical components of LBCS to investigate through ablation studies are:

1.  **The Lexicographic Optimization Strategy:** The paper explicitly contrasts its lexicographic approach with a simple weighted combination of objectives, arguing the latter is insufficient due to differing scales and priority issues. An ablation study replacing the lexicographic optimization with a weighted sum would directly test the effectiveness of the proposed priority-based approach.
2.  **The Voluntary Performance Compromise ($\epsilon$):** The parameter $\epsilon$ is introduced to allow slight degradation in the primary objective ($f_1$) to potentially achieve a significantly smaller coreset size ($f_2$) and potentially improve generalization by avoiding overfitting $f_1$. Ablating this parameter by testing different values, including zero, will reveal its impact on the trade-off between performance and coreset size.
3.  **The Coreset Size Optimization:** Traditional coreset selection methods often fix the coreset size beforehand and only optimize for model performance. LBCS, however, optimizes the coreset size as a secondary objective. An ablation study fixing the coreset size to a predefined value (similar to prior work or values found by LBCS) and optimizing only for performance would highlight the benefit of actively minimizing the size within the RCS framework.

These three ablations target the core novelties and design choices of the LBCS method for the RCS problem. The primary metrics used in the paper and relevant for these ablations are model performance (likely test accuracy or loss) and the final coreset size.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Weighted Combination Baseline
- **Ablated Part**: Lexicographic optimization strategy in the outer loop
- **Action**: REPLACE
- **Replacement**: 
  - Weighted sum objective (1-lambda)*f1 + lambda*f2 with lambda=0.1
  - Weighted sum objective (1-lambda)*f1 + lambda*f2 with lambda=0.5
  - Weighted sum objective (1-lambda)*f1 + lambda*f2 with lambda=0.9
- **Metrics**: Test Accuracy, Coreset Size

### Impact of Performance Compromise Epsilon
- **Ablated Part**: Voluntary performance compromise parameter epsilon
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.01
  - 0.05
  - 0.1
- **Metrics**: Test Accuracy, Coreset Size

### Fixed Coreset Size Baseline
- **Ablated Part**: Coreset size optimization objective (f2) and variable size constraint
- **Action**: REPLACE
- **Replacement**: 
  - Fix coreset size to a small value (e.g., 1% of dataset)
  - Fix coreset size to a medium value (e.g., 5% of dataset)
  - Fix coreset size to a large value (e.g., 10% of dataset)
- **Metrics**: Test Accuracy, Coreset Size

</div>