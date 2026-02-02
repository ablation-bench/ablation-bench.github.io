<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/BiQAP__Neural_Bi_level_Optimization_based_Framework_for_Solving_Quadratic_Assignment_Problems

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "BiQAP: Neural Bi-level Optimization-based Framework for Solving Quadratic Assignment Problems" proposes a novel bi-level unsupervised framework for solving KBQAP instances. The core idea is to use a neural network (FormulaNet) to transform the original QAP instance matrices (F1, F2, Kp) into new matrices (F1^theta, F2^theta, Kp^theta), and then solve an *entropic regularized* QAP problem defined by these new matrices using a differentiable iterative solver (Gromov-Sinkhorn). The parameters of the FormulaNet are trained end-to-end by minimizing the objective function of the *original* QAP instance. The inner solver is initialized with Gumbel samples to help escape local optima.

The paper includes an ablation study in Appendix B (Table 7) and sampling tests in Appendix C (Table 8). The existing ablations investigate:
1.  Removing the FormulaNet ("BiQAP w/o FN"), showing its importance in learning a better instance for the solver.
2.  Varying the number of outer/inner iterations in the differentiable QAP solver, demonstrating robustness to this hyperparameter.
3.  Varying the Gumbel sampling size, showing that performance is primarily due to the method's design rather than excessive sampling.

Based on the method's description and the existing ablations, two important components/design choices that were not explicitly ablated are:

1.  **The Entropic Regularization Coefficient (epsilon):** The inner optimization problem is an *entropic* regularized QAP. The coefficient epsilon controls the strength of this regularization. This is a key hyperparameter defining the inner problem that the differentiable solver optimizes. Understanding how different values of epsilon affect the performance would shed light on the role of this specific regularization in the learned inner problem and the overall framework's performance. The paper mentions epsilon acts like a temperature parameter in a related context (Eq 3), but its specific impact in the BiQAP framework (Eq 4/5) is not analyzed.
2.  **The FormulaNet Architecture:** The paper uses a Mamba-based architecture for the FormulaNet and mentions that other architectures like Linear Attention could also be used. While the "BiQAP w/o FN" ablation shows the necessity of having a network to transform the instance, it doesn't validate the choice of the specific Mamba architecture. Ablating the FormulaNet architecture by replacing Mamba with alternative network structures (e.g., Linear Attention, or a simpler MLP operating on flattened matrices) would help determine if the specific properties of Mamba are crucial or if any sufficiently powerful network capable of mapping matrix inputs to matrix outputs suffices. Given the paper's emphasis on handling large-scale problems, comparing Mamba to other scalable architectures like Linear Attention is particularly relevant.

These two ablations are important because they probe core aspects of the proposed method: the formulation of the learned inner problem (epsilon) and the design of the network that learns this transformation (FormulaNet architecture). They would provide further insights into why BiQAP performs well. I will suggest these two as missing ablations, ranked by their perceived importance to the core formulation. Ablating epsilon seems slightly more fundamental to the mathematical structure of the learned problem.

The metrics used in the paper for evaluation include objective score (obj), gap (difference from a reference objective), accuracy (acc) for GED, and time (Time(sec/100it)). I will include these relevant metrics in the suggested ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Entropic Regularization Epsilon
- **Ablated Part**: Entropic regularization coefficient (epsilon) in the inner optimization problem
- **Action**: REPLACE
- **Replacement**: 
  - 0.01
  - 0.1
  - 1.0
  - 10.0
- **Metrics**: OBJ, GAP, ACC, Time(sec/100it)

### Ablation on FormulaNet Architecture
- **Ablated Part**: Architecture of the FormulaNet
- **Action**: REPLACE
- **Replacement**: 
  - Linear Attention
  - MLP on flattened matrices
- **Metrics**: OBJ, GAP, ACC, Time(sec/100it)

</div>