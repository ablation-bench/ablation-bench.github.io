<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/foa

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes Forward-Optimization Adaptation (FOA), a test-time adaptation method that avoids backpropagation and model weight modification, making it suitable for resource-limited devices and quantized models. The core components of FOA are:
1.  **Forward-Only Prompt Adaptation:** Optimizing a newly added input prompt using the derivative-free CMA-ES optimizer guided by a novel unsupervised fitness function.
2.  **Back-to-Source Activation Shifting:** Directly adjusting the final layer's activations to align them with source domain statistics.

To understand the contribution of these components to FOA's performance, especially its reported superiority over gradient-based methods like TENT even on quantized models, several ablation studies are crucial.

The proposed ablation studies are designed to isolate the impact of the activation shifting mechanism, the individual terms within the novel fitness function used for prompt optimization, the overall contribution of the prompt adaptation itself, and the effect of the prompt's design (its length).

1.  **Ablating Activation Shifting:** This mechanism is applied after the prompt adaptation and directly modifies features. Removing it will show its independent contribution to performance improvement.
2.  **Ablating Fitness Function Components:** The fitness function combines prediction entropy and activation statistics discrepancy. Ablating each term separately will reveal their respective importance in guiding the CMA-ES optimization for the prompt. The statistics discrepancy term is particularly novel for stabilizing CMA in this unsupervised setting.
3.  **Ablating Prompt Adaptation:** Removing the entire prompt optimization part (leaving only activation shifting) will demonstrate the combined benefit of the CMA-ES-based prompt learning.
4.  **Varying Prompt Length:** The prompt is the only learnable parameter in the optimization loop. Investigating different prompt lengths ($N_p$) will show the sensitivity of the method to the capacity of the learnable input.

These studies cover the main novel aspects of FOA and are ranked by their perceived importance in explaining the method's effectiveness. The primary metric used in the paper to evaluate adaptation performance is Average Accuracy, particularly on benchmarks like ImageNet-C, ImageNet-R, and ImageNet-A.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### FOA w/o Activation Shifting
- **Ablated Part**: Back-to-Source Activation Shifting mechanism
- **Action**: REMOVE
- **Metrics**: Average Accuracy

### FOA w/o Statistics Discrepancy Fitness
- **Ablated Part**: Statistics discrepancy term in the fitness function
- **Action**: REMOVE
- **Metrics**: Average Accuracy

### FOA w/o Entropy Fitness
- **Ablated Part**: Prediction entropy term in the fitness function
- **Action**: REMOVE
- **Metrics**: Average Accuracy

### Activation Shifting Only
- **Ablated Part**: Forward-Only Prompt Adaptation mechanism (CMA-ES optimization of prompt)
- **Action**: REMOVE
- **Metrics**: Average Accuracy

### FOA with varied Prompt Length
- **Ablated Part**: Number of prompt embeddings (Np)
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 2
  - 4
  - 8
- **Metrics**: Average Accuracy

</div>