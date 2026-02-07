<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Zero_Shot_Video_Sampling_from_Image

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes ZS² (Zero-Shot Video Sampling), which has two main components:
1. Dependency Noise Model - Controls content consistency between frames using KL divergence
2. Temporal Momentum Attention - Maintains motion coherence using momentum-based attention

Looking at the existing ablations in the paper:
- They compare their method against baselines like Text2Video-Zero
- They show qualitative results with different diffusion models
- They analyze convergence of their two-stage noise algorithm
- They show effects of different λ and μ values on motion control

However, I notice two critical missing ablations:

1. The most important missing ablation is isolating the contribution of each main component (Dependency Noise Model vs Temporal Momentum Attention). This would help understand which component contributes more to the final performance.

2. The second important missing ablation is testing different KL divergence thresholds in the dependency noise model. The paper uses a fixed λ=0.01 but doesn't justify this choice or explore alternatives.

These ablations would provide crucial insights into the method's key components and design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Component Isolation Study
- **Ablated Part**: Main components of ZS²
- **Action**: REMOVE
- **Metrics**: CLIP score, FID

### KL Divergence Threshold Study
- **Ablated Part**: KL divergence threshold λ in dependency noise model
- **Action**: REPLACE
- **Replacement**: 
  - 0.001
  - 0.01
  - 0.1
  - 1.0
- **Metrics**: CLIP score, FID

</div>