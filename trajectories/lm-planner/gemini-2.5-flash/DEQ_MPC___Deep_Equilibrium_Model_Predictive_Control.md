<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/DEQ_MPC___Deep_Equilibrium_Model_Predictive_Control

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "DEQ-MPC: Deep Equilibrium Model Predictive Control" proposes a novel framework that unifies neural network inference and MPC optimization into a joint fixed-point problem, solved by alternating between network forward passes and MPC solver iterations. This contrasts with standard differentiable MPC which treats the solver as a black-box layer.

The core components of DEQ-MPC include the joint fixed-point formulation, the choice of neural network architecture (standard feedforward or DEQ), the iterative Augmented Lagrangian (AL) solver (MPC-m), the number of alternating DEQ-MPC iterations (N) and inner AL iterations (m), the loss function computed on multiple intermediate iterates, and the leveraging of warm-starting.

The paper presents several ablation studies in Section 5.2 and Appendix A.1, investigating the impact of dataset size, network capacity, constraint hardness, time horizon, the effect of parameter updates across AL iterations, training stability related to gradients (comparing intermediate vs final iterate loss implicitly), MPC parameter sensitivity, and the effect of warm-starting with varying numbers of evaluation iterations.

While these ablations cover important aspects, two key areas related to the core mechanism and training procedure are not explicitly ablated:

1.  **The specific number of alternating DEQ-MPC iterations (N) and inner AL iterations (m) used *during training*:** The paper states they use N=6 and m=2 as default values for all experiments (Lines 244-247). Figure 7 shows the performance when evaluating with different numbers of iterations, highlighting the warm-starting benefit. However, the impact of varying N and m *during the training process* on the final performance, training stability, and convergence speed is not shown. This is a critical design choice that affects the computational cost per training step and the overall training dynamics. An ablation varying these parameters during training would provide valuable insight into the trade-off between computational effort and model performance, and justify the chosen default values.

2.  **The number of intermediate AL iterates included in the loss function:** The paper introduces the technique of computing losses on "multiple unconverged intermediate iterates" (Equation 15, Lines 308-315) to improve gradient quality and training stability. Figure 5 demonstrates the benefit of this approach by comparing DEQ-MPC-DEQ (which uses intermediate losses) against Diff-MPC-DEQ (which uses only the final iterate loss). However, the paper does not ablate *how many* intermediate iterates are included in the loss calculation (the upper limit `I` in Equation 15). Is using *all* intermediate iterates necessary, or would a smaller subset suffice? Ablating this parameter would quantify the contribution of including different numbers of intermediate iterates to the final performance and stability.

These two missing ablations are important because they directly relate to the computational characteristics and the novel training methodology of DEQ-MPC. Understanding the sensitivity to the number of iterations and the specific loss formulation is crucial for practical implementation and further development of the method. I rank the ablation on the number of alternating iterations slightly higher as it directly impacts the core alternating fixed-point solving process.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Effect of Alternating Iteration Count
- **Ablated Part**: Number of outer DEQ-MPC iterations (N) and inner AL iterations (m) performed during training.
- **Action**: REPLACE
- **Replacement**: 
  - {'N': 3, 'm': 2}
  - {'N': 6, 'm': 1}
  - {'N': 6, 'm': 4}
  - {'N': 10, 'm': 2}
- **Metrics**: Validation Error, Returns

### Effect of Loss Iterates
- **Ablated Part**: Number of intermediate AL iterates included in the loss function.
- **Action**: REPLACE
- **Replacement**: 
  - {'loss_iterates': 1}
  - {'loss_iterates': 'N'}
  - {'loss_iterates': 'N*m'}
- **Metrics**: Validation Error, Returns

</div>