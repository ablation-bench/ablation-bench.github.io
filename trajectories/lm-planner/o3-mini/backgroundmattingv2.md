<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/backgroundmattingv2

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

In our ablation plan we focus on investigating the key components that contribute to both the quality and efficiency of the Real-Time High-Resolution Background Matting method. The first study removes the refinement network entirely so that we can measure the necessity of the two-stage approach by comparing the coarse result from the base network to the refined final output. Next, we isolate the patch-selection strategy by replacing the error prediction–driven selection mechanism with random or uniform selection, in order to understand the impact of targeted refinement on matting quality and runtime. Third, we study the effect of the parameter k (the number of patches refined) by testing various values (e.g., 1000, 5000, 10000) to analyze the trade-off between runtime efficiency and detail recovery. Fourth, the backbone network is a critical component and we propose replacing the ResNet-50 encoder with alternative architectures (ResNet-101, MobileNetV2) to evaluate the balance between speed and quality. Finally, since the network uses an ASPP module for multi-scale feature aggregation, we ablate this module by removing it to study its influence on fine-detailed matting quality. All these studies would report the quality of the computed alpha matte and foreground (via L1 errors and gradient-based metrics) as well as runtime performance (FPS).
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Removal of Refinement Network
- **Ablated Part**: The refinement network that refines high-resolution patches selected via the error prediction map
- **Action**: REMOVE
- **Metrics**: L1 alpha error, Gradient error, FPS

### Error Map vs. Random Patch Selection
- **Ablated Part**: The error prediction module used for selecting refinement patches
- **Action**: REPLACE
- **Replacement**: 
  - Random patch selection
  - Uniform grid selection
- **Metrics**: L1 alpha error, Gradient error, FPS

### Varying Patch Refinement Count (k)
- **Ablated Part**: The number of patches (k) selected for high-resolution refinement
- **Action**: REPLACE
- **Replacement**: 
  - k=1000
  - k=5000
  - k=10000
- **Metrics**: L1 alpha error, Foreground L1 error, FPS

### Backbone Architecture Study
- **Ablated Part**: The encoder backbone in the base network for feature extraction
- **Action**: REPLACE
- **Replacement**: 
  - ResNet-50
  - ResNet-101
  - MobileNetV2
- **Metrics**: L1 alpha error, Foreground L1 error, FPS

### Removal of ASPP Module
- **Ablated Part**: The ASPP module used for multi-scale context aggregation in the base network
- **Action**: REMOVE
- **Metrics**: L1 alpha error, Gradient error, FPS

</div>