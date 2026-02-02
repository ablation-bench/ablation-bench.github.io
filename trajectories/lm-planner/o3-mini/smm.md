<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/smm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The following ablation studies are proposed to identify the impact of the key components in SMM. First, we compare the core idea by replacing the sample‐specific mask generator with a fixed shared mask (Ablation A), which directly tests whether per-sample adaptation is beneficial over the shared mask used in prior works. Next, we test the multi-channel design by replacing the three‐channel mask with a simple binary mask (Ablation B) in order to evaluate the contribution of richer mask representations. Third, we investigate the patch-wise interpolation module by replacing it with standard interpolation methods (Ablation C) to see if the simplified gradient computation and patch consistency bring advantages. Moreover, we study the impact of the mask generator architecture itself by replacing the lightweight CNN with a simpler MLP or fully connected network (Ablation D), which will help assess the importance of spatially localized features. Lastly, we explore whether combining a shared noise pattern with a sample-specific mask is beneficial, by replacing it with a direct sample-specific noise pattern generation (Ablation E), as suggested by the discussion on approximation errors. The metrics chosen are those reported in the paper, including classification accuracy and other learning indicators such as approximation error, training loss, gradient stability, convergence rate, and model parameter count.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A: Shared vs. Sample-specific Masks
- **Ablated Part**: The sample-specific mask generator mechanism; replacing it with a fixed shared mask across all samples
- **Action**: REPLACE
- **Replacement**: 
  - fixed shared mask
- **Metrics**: classification accuracy, approximation error, training loss

### Ablation B: Multi-channel Mask Design
- **Ablated Part**: The three-channel mask representation; replacing it with a single-channel binary mask
- **Action**: REPLACE
- **Replacement**: 
  - binary mask
- **Metrics**: classification accuracy, approximation error

### Ablation C: Interpolation Method
- **Ablated Part**: The patch-wise interpolation module used to upscale masks; replacing it with standard interpolation techniques
- **Action**: REPLACE
- **Replacement**: 
  - bilinear interpolation
  - nearest-neighbor interpolation
- **Metrics**: classification accuracy, gradient stability, convergence time

### Ablation D: Mask Generator Architecture
- **Ablated Part**: The lightweight CNN used for generating sample-specific masks; replacing it with a simpler architecture
- **Action**: REPLACE
- **Replacement**: 
  - simple MLP
  - fully connected network
- **Metrics**: classification accuracy, model parameter count, convergence rate

### Ablation E: Shared Noise vs. Direct Sample-specific Noise
- **Ablated Part**: The use of a shared noise pattern δ modulated by the sample-specific mask; replacing it with direct sample-specific noise pattern generation
- **Action**: REPLACE
- **Replacement**: 
  - direct sample-specific noise pattern
- **Metrics**: classification accuracy, approximation error

</div>