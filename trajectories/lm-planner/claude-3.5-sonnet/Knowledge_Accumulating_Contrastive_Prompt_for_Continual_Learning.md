<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Knowledge_Accumulating_Contrastive_Prompt_for_Continual_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

First, let me analyze the existing ablations in the paper:
1. The paper includes ablations on hyperparameters λctr and λprev that control the contribution of contrastive and previous knowledge transfer losses
2. There are ablations on prompt length lp
3. They compare against related contrastive learning and knowledge distillation methods

Looking at the key components of their method:
1. The main novelty is using a single accumulating prompt vs a prompt pool
2. They use two key losses: Lctr (contrastive loss between current and previous prompts) and Lprev (knowledge transfer through embedding space)
3. The method relies on treating prompt-augmented inputs as positive pairs

I notice two important missing ablations that would help validate key design choices:

1. The choice of positive pairs - they treat inputs with current and previous prompts as positive pairs, but don't validate if this is optimal. Alternative formulations of positive pairs could be explored.

2. The architecture of the projection/prediction networks (W and Wq) - while they use simple linear layers with batch norm, they don't ablate different architectures which could significantly impact performance.

These ablations would help validate core components of their method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Positive Pair Formulation Ablation
- **Ablated Part**: The way positive pairs are constructed from prompt-augmented inputs
- **Action**: REPLACE
- **Replacement**: 
  - Random prompt pairs
  - Multiple previous prompts
  - Cross-task prompt pairs
- **Metrics**: Average Accuracy, Forgetting

### Projection Network Architecture Ablation
- **Ablated Part**: Architecture of projection (W) and prediction (Wq) networks
- **Action**: REPLACE
- **Replacement**: 
  - MLP with varying depths
  - Non-linear activations
  - Different normalization schemes
- **Metrics**: Average Accuracy, Forgetting

</div>