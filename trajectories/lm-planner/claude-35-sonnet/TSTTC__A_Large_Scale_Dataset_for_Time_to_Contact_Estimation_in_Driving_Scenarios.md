<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/TSTTC__A_Large_Scale_Dataset_for_Time_to_Contact_Estimation_in_Driving_Scenarios

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Looking at the paper, the authors propose a dataset and two main methods for TTC estimation:
1. Pixel MSE - which measures similarity between frames in image space
2. Deep Scale - which uses a neural network to extract features and measure similarity

The paper includes several ablation studies:
- Number of scale bins
- Center shift operation
- NeRF data augmentation
- Target size for grid sampling
- Kernel size
- Plate blur
- Number of frame gaps

However, there are some important aspects that were not ablated:

1. The choice of backbone architecture for Deep Scale is not explored. The authors use a modified CSPNet but don't justify this choice or compare to alternatives.

2. The similarity measurement approach in Deep Scale uses cosine similarity between feature maps, but other similarity metrics could potentially work better.

These represent core design choices that could significantly impact the method's performance.

I'll suggest these as missing ablation studies, ranked by importance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Backbone Architecture Ablation
- **Ablated Part**: CSPNet backbone in Deep Scale method
- **Action**: REPLACE
- **Replacement**: 
  - ResNet-18
  - MobileNetV2
  - EfficientNet-B0
- **Metrics**: MiD, RTE, inference time

### Feature Similarity Metric Ablation
- **Ablated Part**: Cosine similarity for feature map comparison in Deep Scale
- **Action**: REPLACE
- **Replacement**: 
  - L1 distance
  - L2 distance
  - Pearson correlation
- **Metrics**: MiD, MiDc, MiDs, MiDl, MiDn, RTE

</div>