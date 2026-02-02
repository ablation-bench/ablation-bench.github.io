<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Bayesian_Policy_Distillation_via_Offline_RL_for_Lightweight_and_Fast_Inference

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents an innovative method for compressing teacher policies through Bayesian policy distillation using offline RL. The existing ablation in the paper focuses on analyzing the impact of the sparsity threshold (CThreshold) and contrasts performance with online RL methods that use small student networks without guidance from a teacher. However, two critical aspects remain unexplored:
1. The contribution of the Bayesian modeling itself. The method leverages a Bayesian neural network (via variational dropout) to capture weight uncertainty and induce sparsity. A missing ablation is to remove or replace the Bayesian mechanism with a standard deterministic counterpart. This experiment would clarify the contribution of learning weight uncertainty in preserving performance while achieving high sparsity and reducing memory footprint.
2. The impact of the KL divergence term’s annealing schedule in the loss function. The paper uses a linear annealing strategy for η to gradually impose sparsity, yet it does not compare alternative schedules. Testing different annealing schemes (e.g., constant, exponential) could reveal how sensitive the method is to this hyperparameter and whether improved trade-offs between performance and sparsity might be achieved.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Bayesian Uncertainty
- **Ablated Part**: Bayesian neural network weight uncertainty and variational dropout mechanism used in the student policy
- **Action**: REMOVE
- **Metrics**: Normalized Performance, Inference Time, Sparsity, Memory Footprint

### Ablation: KL Annealing Schedule
- **Ablated Part**: KL divergence annealing strategy (η schedule) for imposing sparsity in the loss function
- **Action**: REPLACE
- **Replacement**: 
  - constant η
  - exponential annealing
  - linear annealing (baseline)
- **Metrics**: Normalized Performance, Training Stability, Sparsity

</div>