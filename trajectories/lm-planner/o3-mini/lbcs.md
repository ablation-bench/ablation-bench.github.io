<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/lbcs

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose the following five ablation studies to identify and quantify the contribution of key components in our refined coreset selection method. The most critical aspect is the novel lexicographic bilevel formulation that prioritizes model performance (f1) over coreset size (f2). In our first study, we replace this lexicographic ordering with a weighted combination scheme using various lambda values, to quantify how much the explicit priority order benefits the final coreset quality and model performance. The second study investigates the effect of the voluntary performance compromise parameter (epsilon) that permits slight relaxations in the primary objective (f1) in order to further minimize the coreset size. In the third study, we examine the inner-loop training strategy by comparing the warm‐start (fine-tuning from previous masks) against training from scratch, thereby assessing the impact on convergence behavior and computational efficiency. The fourth study explores the outer-loop optimization mechanism by replacing the randomized direct search with alternative black‐box methods (e.g. grid search, genetic algorithm, simulated annealing) to understand its influence on convergence and stability. Finally, the fifth study evaluates the grouping strategy used to accelerate the outer-loop mask updates by varying the group size (or even removing grouping) to see how it affects both solution quality (f1 and f2) and overall computation time. Together, these ablation studies provide a clear picture of the role and importance of each component in our approach.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Lexicographic vs Weighted Combination
- **Ablated Part**: The outer-loop optimization strategy: replacing the lexicographic ordering (prioritized f1 over f2) with a weighted combination of objectives.
- **Action**: REPLACE
- **Replacement**: 
  - weighted combination (lambda=0.1)
  - weighted combination (lambda=0.3)
  - weighted combination (lambda=0.5)
- **Metrics**: f1, f2, test_accuracy

### Performance Compromise Parameter Ablation
- **Ablated Part**: The voluntary performance compromise parameter (epsilon) that sets a tolerance for f1 to allow further minimization of f2.
- **Action**: REPLACE
- **Replacement**: 
  - epsilon=0.0
  - epsilon=0.01
  - epsilon=0.05
  - epsilon=0.1
- **Metrics**: f1, f2

### Inner-loop Training Strategy Ablation
- **Ablated Part**: The inner-loop model training method: comparing warm-start (fine-tuning from previous mask) versus training from scratch for each mask update.
- **Action**: REPLACE
- **Replacement**: 
  - warm-start
  - training from scratch
- **Metrics**: f1, f2, training_time

### Outer-loop Optimization Method Ablation
- **Ablated Part**: The black-box optimization strategy in the outer loop for mask updates: testing alternative algorithms.
- **Action**: REPLACE
- **Replacement**: 
  - grid search
  - genetic algorithm
  - simulated annealing
- **Metrics**: f1, f2, convergence_speed

### Grouping Strategy Ablation
- **Ablated Part**: The grouping mechanism that forces multiple examples to share a mask for outer-loop speed-up, evaluating its effect on solution quality and computation efficiency.
- **Action**: REPLACE
- **Replacement**: 
  - no grouping
  - group size 5
  - group size 10
  - group size 20
- **Metrics**: f1, f2, computation_time

</div>