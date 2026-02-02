<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Improving_the_Transferability_of_Adversarial_Attacks_through_Experienced_Precise_Nesterov_Momentum

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes two main components:
1. Experienced Momentum (EM) - Pre-trained momentum initialized from training on models derived using Random Channels Swapping (RCS)
2. Precise Nesterov momentum (PN) - Refined pre-update considering current gradient

The paper includes ablation studies on:
- Impact of decay factor μ and number of pre-training epochs
- Individual impact of EM and PN vs combined EPN

However, there are some important missing ablations that could provide deeper insights:

1. The impact of Random Channels Swapping (RCS) strategy:
- The paper uses RCS to derive models for training EM but doesn't ablate this choice
- Testing different model derivation strategies would validate if RCS is optimal
- This is important since RCS directly affects how generalizable the pre-trained momentum is

2. The gradient accumulation strategy in PN:
- PN refines pre-updates by considering current gradient but the paper doesn't analyze different ways to combine/weight the gradients
- Understanding the optimal gradient combination strategy is crucial since it directly impacts the precision of updates
- This ablation would help understand if the current simple addition is optimal

I'll focus on these two ablations as they target core components of the method that lack proper validation in the paper.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### RCS Strategy Ablation
- **Ablated Part**: Random Channels Swapping strategy for deriving models to train EM
- **Action**: REPLACE
- **Replacement**: 
  - Random Cropping
  - Random Rotation
  - Random Scaling
  - No transformation (baseline)
- **Metrics**: Attack Success Rate, Average Transferability Rate

### Gradient Combination Strategy
- **Ablated Part**: Addition of current gradient in Precise Nesterov momentum
- **Action**: REPLACE
- **Replacement**: 
  - Weighted sum with learnable weights
  - Exponential moving average
  - Momentum-based combination
- **Metrics**: Attack Success Rate, Average Transferability Rate

</div>