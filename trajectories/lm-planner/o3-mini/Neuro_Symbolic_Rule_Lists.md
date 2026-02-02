<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Neuro_Symbolic_Rule_Lists

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We identified two important components that are central to the success of NYRULES but were not explicitly ablated in the paper. First, although the method relies on a temperature annealing schedule to gradually convert soft threshold predicates and rule ordering into their discrete counterparts, the paper does not report an ablation study comparing this annealing schedule with a setting where the temperature is held constant. Evaluating a constant temperature setting (with various fixed values) will highlight the importance of employing an annealing schedule to obtain crisp rules and proper gradient flow, as measured by classification accuracy and F1 score.

Second, NYRULES includes a minimum-support regularization term to guarantee that every rule covers a sufficient—but not excessive—amount of data. Although the paper shows ablations of thresholding (using different pre-processing methods) and the relaxed versus hard conjunction design, it does not investigate the effect of completely removing this support regularizer from the overall loss. This ablation study would reveal how critical the minimum-support constraint is for ensuring meaningful and interpretable rule usage, as reflected in overall F1 score and possibly other rule quality metrics such as coverage balance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Constant Temperature Ablation
- **Ablated Part**: Temperature annealing schedule for both soft predicates and rule list ordering (Gumbel-Softmax)
- **Action**: REPLACE
- **Replacement**: 
  - Fixed t_pi = 0.2
  - Fixed t_pi = 0.05
  - Fixed t_rl = 1.0
  - Fixed t_rl = 0.1
- **Metrics**: F1 score, Accuracy

### Minimum-Support Regularizer Ablation
- **Ablated Part**: Minimum-support regularization term in the objective that forces non-trivial rule coverage
- **Action**: REMOVE
- **Metrics**: F1 score, Rule coverage, Interpretability (rule sparsity)

</div>