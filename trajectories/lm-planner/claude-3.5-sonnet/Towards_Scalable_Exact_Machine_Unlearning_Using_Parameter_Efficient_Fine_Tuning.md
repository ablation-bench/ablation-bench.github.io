<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Towards_Scalable_Exact_Machine_Unlearning_Using_Parameter_Efficient_Fine_Tuning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

First, let me identify the key components of the S3T method and the ablations that were already conducted:

1. The paper already conducted ablations on:
- Layer allocation per slice (Fig 13)
- Sequence-based vs S3T training comparison (Fig 14)
- Impact of ensemble size (Fig 16)
- Comparison of sequence selection algorithms (BMS vs cyclic rotation)

Key components that could benefit from additional ablation studies:

1. The sequential top-to-bottom layer training strategy:
The authors mention in Section C.2 that they chose top-to-bottom training because "top layers were easier to train at the start and a bottom-up approach didn't converge". However, there's no formal ablation studying different layer ordering strategies.

2. The cumulative slice training approach:
The authors mention they train layers in a cumulative manner where the i-th layer is trained using slices {1,...,i}, but don't provide ablation evidence for why this is better than non-cumulative approaches.

I'll suggest these two as the most important missing ablations since they represent core design choices in the method that lack empirical validation.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Layer Training Order Ablation
- **Ablated Part**: Sequential top-to-bottom layer training strategy
- **Action**: REPLACE
- **Replacement**: 
  - bottom-to-top training
  - random layer order training
  - middle-out training
- **Metrics**: model performance (accuracy/F1), training convergence rate, deletion rate

### Slice Accumulation Strategy Ablation
- **Ablated Part**: Cumulative slice training approach
- **Action**: REPLACE
- **Replacement**: 
  - single-slice per layer (non-cumulative)
  - sliding window of k slices
  - random slice subset per layer
- **Metrics**: model performance (accuracy/F1), deletion rate, training time

</div>