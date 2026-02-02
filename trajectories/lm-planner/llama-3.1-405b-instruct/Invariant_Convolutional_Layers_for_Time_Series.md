<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Invariant_Convolutional_Layers_for_Time_Series

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Invariant Convolutional Layers for Time Series" proposes a novel approach to time series analysis by introducing invariant convolutional layers that can capture complex patterns in time series data while being robust to certain transformations, such as offset shift and scaling, and linear trend and scaling. The authors mathematically formulate the concept of invariance in time series and design a locally invariant embedding to some deformations, extracted via convolutions. They also propose a strategy that restricts, by learning, the convolutional layer to the relevant invariances for a given task.

The paper presents an example architecture, the INVCONVNET model, which combines the proposed invariant convolutions with standard (or variant) convolutions in a single embedding layer. The model is experimentally tested on time series classification and anomaly detection tasks, and the results show that it achieves superior performance against common baselines.

A missing ablation study in this paper is the investigation of the impact of the number of invariant convolutional layers on the performance of the INVCONVNET model. Another missing ablation study is the comparison of the performance of the INVCONVNET model with different types of invariant convolutions, such as those invariant to offset shift and scaling, and those invariant to linear trend and scaling.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: number of invariant convolutional layers
- **Action**: REMOVE
- **Metrics**: accuracy, F1-score

### Ablation B
- **Ablated Part**: type of invariant convolutions
- **Action**: REPLACE
- **Replacement**: 
  - invariant to offset shift and scaling
  - invariant to linear trend and scaling
- **Metrics**: accuracy, F1-score

</div>