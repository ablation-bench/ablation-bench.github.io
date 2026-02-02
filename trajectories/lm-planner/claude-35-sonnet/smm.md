<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/smm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, SMM has several key components that warrant investigation through ablation studies:

1. The most critical component is the sample-specific nature of the masks, which is the main novelty and contribution. Testing this against a shared mask would validate the core thesis.

2. The three-channel mask design is another important feature that differs from traditional binary masks. Testing single-channel vs. three-channel masks would reveal the value of this design choice.

3. The lightweight ConvNet architecture used for mask generation is a key architectural choice. Testing different architectures or removing it entirely would show its importance.

4. The patch-wise interpolation module is used to handle size inconsistencies. Testing alternative interpolation methods would validate this design choice.

5. The shared pattern δ across all samples is maintained while making masks sample-specific. Testing sample-specific patterns would validate this design choice.

I'll rank these in order of importance and format them as ablation suggestions.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Shared vs. Sample-specific Masks
- **Ablated Part**: Sample-specific mask generation
- **Action**: REPLACE
- **Replacement**: 
  - single shared binary mask
  - single shared three-channel mask
- **Metrics**: classification accuracy, training loss, approximation error

### Mask Channel Ablation
- **Ablated Part**: Three-channel mask design
- **Action**: REPLACE
- **Replacement**: 
  - single-channel binary mask
  - single-channel continuous mask
- **Metrics**: classification accuracy, training loss

### Mask Generator Architecture
- **Ablated Part**: Lightweight ConvNet mask generator
- **Action**: REPLACE
- **Replacement**: 
  - MLP generator
  - larger ConvNet
  - smaller ConvNet
- **Metrics**: classification accuracy, parameter count, training time

### Interpolation Method
- **Ablated Part**: Patch-wise interpolation module
- **Action**: REPLACE
- **Replacement**: 
  - bilinear interpolation
  - nearest neighbor interpolation
- **Metrics**: classification accuracy, training efficiency

### Pattern Sharing
- **Ablated Part**: Shared pattern δ
- **Action**: REPLACE
- **Replacement**: 
  - sample-specific patterns
  - class-specific patterns
- **Metrics**: classification accuracy, parameter count, training loss

</div>