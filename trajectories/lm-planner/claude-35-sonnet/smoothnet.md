<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/smoothnet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, SmoothNet is a temporal-only refinement network that aims to reduce jitters in human pose estimation. The key components that warrant investigation through ablation studies are:

1. The motion-aware architecture - The paper introduces velocity and acceleration branches which should be validated.

2. The temporal modeling approach - The authors chose FCN over TCN and Transformer, which needs validation.

3. The loss function components - The paper uses both pose and acceleration losses.

4. The temporal window size - This is a critical hyperparameter that affects the model's ability to capture long-range dependencies.

5. The independence of joint processing - The model processes each axis independently.

I'll suggest ablation studies to validate these key design choices, focusing on the most important aspects first.

The metrics used in the paper are:
- MPJPE (Mean Per Joint Position Error) for accuracy
- Accel (Mean Per Joint Acceleration Error) for smoothness
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Motion-Aware Architecture Ablation
- **Ablated Part**: velocity and acceleration branches
- **Action**: REMOVE
- **Metrics**: MPJPE, Accel

### Temporal Modeling Ablation
- **Ablated Part**: FCN backbone
- **Action**: REPLACE
- **Replacement**: 
  - TCN
  - Transformer
- **Metrics**: MPJPE, Accel

### Loss Function Ablation
- **Ablated Part**: acceleration loss
- **Action**: REMOVE
- **Metrics**: MPJPE, Accel

### Window Size Ablation
- **Ablated Part**: temporal window size T
- **Action**: REPLACE
- **Replacement**: 
  - 8
  - 16
  - 32
  - 64
  - 128
- **Metrics**: MPJPE, Accel

### Joint Processing Ablation
- **Ablated Part**: independent joint axis processing
- **Action**: REPLACE
- **Replacement**: 
  - joint processing of all axes
- **Metrics**: MPJPE, Accel

</div>