<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/foa

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces a novel method called Forward-Optimization Adaptation (FOA) for test-time model adaptation without backpropagation, which is particularly useful for resource-limited devices. The method involves two main components: prompt adaptation using a derivative-free optimizer and an activation shifting scheme. The ablation studies should focus on these components to understand their individual contributions to the overall performance.

1. **Prompt Adaptation**: The FOA method uses a newly added prompt as the model's input, which is optimized using a covariance matrix adaptation evolution strategy. An ablation study could involve removing this prompt adaptation to see how much it contributes to the model's performance.

2. **Fitness Function**: The fitness function in FOA combines prediction entropy and activation statistics discrepancy. An ablation study could replace this fitness function with simpler alternatives, such as using only prediction entropy, to evaluate the importance of the activation statistics discrepancy.

3. **Activation Shifting Scheme**: This scheme adjusts the model activations to align test samples with the source training domain. An ablation study could remove this component to assess its impact on adaptation performance.

4. **Quantization Impact**: The paper highlights the use of quantized models (8-bit ViT) in FOA. An ablation study could compare the performance of FOA on quantized versus full-precision models to understand the trade-offs involved.

5. **Population Size in CMA-ES**: The population size in the covariance matrix adaptation evolution strategy could be varied to see how it affects the optimization process and the final model performance.

These ablation studies will help isolate the effects of each component and provide insights into the design choices made in the FOA method.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Prompt Adaptation
- **Action**: REMOVE
- **Metrics**: accuracy, memory usage

### Ablation 2
- **Ablated Part**: Fitness Function
- **Action**: REPLACE
- **Replacement**: 
  - prediction entropy only
  - activation statistics discrepancy only
- **Metrics**: accuracy, stability

### Ablation 3
- **Ablated Part**: Activation Shifting Scheme
- **Action**: REMOVE
- **Metrics**: accuracy, adaptation performance

### Ablation 4
- **Ablated Part**: Quantization Impact
- **Action**: REPLACE
- **Replacement**: 
  - full-precision 32-bit ViT
- **Metrics**: accuracy, memory usage

### Ablation 5
- **Ablated Part**: Population Size in CMA-ES
- **Action**: REPLACE
- **Replacement**: 
  - 10
  - 50
  - 100
- **Metrics**: accuracy, convergence speed

</div>