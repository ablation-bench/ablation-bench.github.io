<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/On_Policy_Policy_Gradient_Reinforcement_Learning_Without_On_Policy_Sampling

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that the authors have conducted several ablation studies, including:
1. Ablating the clipping mechanism (setting ϵPROPS = ∞)
2. Ablating the regularization term (setting λ = 0)
3. Testing different buffer sizes (b)

However, there are two critical components that weren't properly ablated:

1. The behavior batch size (m) - While the authors mention tuning this hyperparameter, they don't provide a systematic ablation study showing its impact. This is crucial since m determines how frequently the behavior policy is updated, which directly affects the method's ability to correct sampling error.

2. The behavior policy architecture - The authors use the same architecture for both target and behavior policies (MLP with hidden layers [64,64]), but don't justify this choice or explore alternatives. Since the behavior policy's role is fundamentally different from the target policy (correcting sampling error vs maximizing returns), different architectures might be more suitable.

These ablations would help understand the method's sensitivity to these important design choices and potentially lead to improvements.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Behavior Batch Size Ablation
- **Ablated Part**: behavior batch size m (frequency of behavior policy updates)
- **Action**: REPLACE
- **Replacement**: 
  - 128
  - 256
  - 512
  - 1024
  - 2048
- **Metrics**: sampling error (KL divergence), return, training time

### Behavior Policy Architecture Ablation
- **Ablated Part**: behavior policy network architecture
- **Action**: REPLACE
- **Replacement**: 
  - smaller MLP [32,32]
  - larger MLP [128,128]
  - different architecture than target policy
- **Metrics**: sampling error (KL divergence), return, training time

</div>