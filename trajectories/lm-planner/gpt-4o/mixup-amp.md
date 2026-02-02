<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/mixup-amp

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces the Adversarial Mixing Policy (AMP) as a method to relax the Locally Linear Constraints in Mixup by adding adversarial perturbations to the mixing coefficients. This approach aims to address the under-fitting issue associated with strict linear constraints in Mixup, especially in low-resource conditions. The AMP method is structured in a "min-max-rand" formulation, which involves three main operations: Rand, Max, and Min. Each of these operations plays a crucial role in the method's performance.

To design effective ablation studies, we should focus on the key components of the AMP method and their contributions to the overall performance. The following ablation studies are suggested:

1. Ablate the adversarial perturbation in the Max operation to understand its impact on relaxing the linear constraints and improving regularization.
2. Explore the effect of different distributions for the mixing coefficient in the Rand operation to see how the choice of distribution affects the generation of synthetic data.
3. Investigate the impact of the step size (ε) used in the Max operation to determine its influence on the adversarial perturbation's effectiveness.
4. Examine the role of the mask-based mechanism in the Min operation to assess its importance in minimizing the loss effectively.
5. Test the integration of AMP with other Mixup variants to evaluate its flexibility and performance in different settings.

These ablation studies will help attribute the performance improvements to specific components of the AMP method and provide insights into potential areas for further optimization.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Adversarial perturbation in Max operation
- **Action**: REMOVE
- **Metrics**: error rate, predictive error rate

### Ablation 2
- **Ablated Part**: Distribution of mixing coefficient in Rand operation
- **Action**: REPLACE
- **Replacement**: 
  - Uniform(0,1)
  - Normal(0.5,0.1)
- **Metrics**: error rate, predictive error rate

### Ablation 3
- **Ablated Part**: Step size (ε) in Max operation
- **Action**: REPLACE
- **Replacement**: 
  - 0.01
  - 0.05
  - 0.1
- **Metrics**: error rate, predictive error rate

### Ablation 4
- **Ablated Part**: Mask-based mechanism in Min operation
- **Action**: REMOVE
- **Metrics**: error rate, predictive error rate

### Ablation 5
- **Ablated Part**: Integration of AMP with other Mixup variants
- **Action**: ADD
- **Replacement**: 
  - Manifold Mixup
  - Nonlinear Mixup
- **Metrics**: error rate, predictive error rate

</div>