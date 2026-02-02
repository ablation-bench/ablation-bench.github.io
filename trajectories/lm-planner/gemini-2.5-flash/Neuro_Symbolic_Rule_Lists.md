<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Neuro_Symbolic_Rule_Lists

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Neuro-Symbolic Rule Lists (NyRules)" introduces an end-to-end differentiable framework for learning interpretable rule lists. Key components include learned feature discretization via soft predicates with temperature annealing (tπ), a differentiable logical conjunction (relaxed harmonic mean), learnable rule priorities with Gumbel-Softmax relaxation and annealing (trl), and a minimum-support regularization term.

The paper presents several ablation studies in Section 5.2 and Appendix F:
1.  **Relaxed Conjunction:** Compares the proposed relaxed conjunction with a strict version (ϵ=0). This shows the importance of the non-vanishing gradient property.
2.  **Thresholding:** Compares the learned discretization with fixed pre-discretization methods (uniform and k-means binning). This highlights the advantage of learning thresholds end-to-end.
3.  **Rule Ordering:** Compares the learned rule priority with a fixed priority. This demonstrates the benefit of optimizing rule order.

These ablations cover crucial aspects like the differentiable conjunction, learned discretization, and learned ordering. However, two other significant components or design choices are central to the method's success and could benefit from further ablation:

1.  **Temperature Annealing Schedule:** The method relies heavily on temperature annealing for both predicate crispness (tπ) and rule list convergence (trl). The paper states that the schedule is crucial (Appendix C.1) and describes the specific linear decay schedule used. An ablation study investigating the impact of different annealing strategies (e.g., no annealing, different decay rates, different start/end temperatures) would be valuable. It would demonstrate how sensitive the method is to this choice and provide stronger justification for the chosen schedule, which is critical for transitioning from the soft, differentiable relaxation to the final crisp rule list.
2.  **Minimum-Support Regularization:** The paper introduces a specific regularization term (λR) to encourage rules with non-trivial coverage. While standard in rule learning, its differentiable formulation and impact within the NyRules framework are not explicitly ablated. An experiment removing this term (λ=0) or varying the regularization weight (λ) would quantify its contribution to the model's performance and potentially its interpretability (by ensuring rules cover a meaningful number of samples).

Based on their importance to the core differentiable learning and convergence process (temperature annealing) and the explicit objective function design (support regularization), these two missing ablations are suggested. The metrics used in the paper's existing ablations (F1 score and Accuracy) are appropriate for evaluating the impact of these components.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Temperature Schedule Ablation
- **Ablated Part**: Temperature annealing schedule for predicate and rule list temperatures
- **Action**: REPLACE
- **Replacement**: 
  - No annealing (fixed temperatures)
  - Different decay rate/schedule
- **Metrics**: F1, Accuracy

### Support Regularization Ablation
- **Ablated Part**: Minimum-Support regularization term (lambda * R)
- **Action**: REPLACE
- **Replacement**: 
  - lambda=0 (remove regularization)
  - Different lambda values (e.g., 0.1, 1.0)
- **Metrics**: F1, Accuracy

</div>