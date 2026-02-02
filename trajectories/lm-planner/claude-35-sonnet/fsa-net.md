<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/fsa-net

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, FSA-Net has several key components that warrant investigation through ablation studies:

1. Fine-grained Structure Mapping: This is one of the most important novel components that spatially groups features before aggregation. Testing its effectiveness is crucial.

2. Scoring Functions: The paper uses three different scoring functions (1x1 conv, variance, uniform) that provide complementary information. Understanding their individual contributions is important.

3. Two-Stream Architecture: The method uses two parallel streams with different activation functions (ReLU vs Tanh). This design choice should be validated.

4. Stage Fusion Module: The fusion of features between streams at each stage is another key architectural component.

5. Soft Stagewise Regression: The regression scheme that divides the prediction into stages is fundamental to the approach.

I'll prioritize the most important ablations that would help validate the key claims and components of the method.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Fine-grained Structure Mapping Ablation
- **Ablated Part**: Fine-grained structure mapping module
- **Action**: REMOVE
- **Metrics**: MAE Yaw, MAE Pitch, MAE Roll

### Scoring Function Comparison
- **Ablated Part**: Scoring function type
- **Action**: REPLACE
- **Replacement**: 
  - 1x1 conv only
  - variance only
  - uniform only
- **Metrics**: MAE Yaw, MAE Pitch, MAE Roll

### Stream Architecture Ablation
- **Ablated Part**: Two-stream architecture
- **Action**: REPLACE
- **Replacement**: 
  - single ReLU stream
  - single Tanh stream
- **Metrics**: MAE Yaw, MAE Pitch, MAE Roll

### Stage Fusion Ablation
- **Ablated Part**: Stage fusion module
- **Action**: REMOVE
- **Metrics**: MAE Yaw, MAE Pitch, MAE Roll

</div>