<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Towards_Infinite_Long_Prefix_in_Transformer

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Towards Infinite-Long Prefix in Transformer" introduces a novel method called NTK-Attention, which aims to approximate infinite-long prefix learning using a finite number of parameters. The paper provides a theoretical analysis using the Neural Tangent Kernel (NTK) framework and demonstrates the method's effectiveness through empirical evaluations on various datasets. The existing ablation studies in the paper focus on the sensitivity of hyper-parameters in NTK-Attention and the computational costs compared to standard prefix learning.

To suggest missing ablation studies, we need to consider the main components of the NTK-Attention method and identify any critical parts that have not been thoroughly investigated. One potential area for ablation is the replacement of the trainable parameters Z and k, which are used to approximate the prefix matrix P. Another area is the polynomial method used for attention approximation, which could be replaced with alternative methods to assess its impact on performance.

The suggested ablation studies aim to provide insights into the importance of these components and their contribution to the overall performance of the NTK-Attention method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Trainable parameters Z and k in NTK-Attention
- **Action**: REPLACE
- **Replacement**: 
  - Random Initialization
  - Zero Initialization
- **Metrics**: Accuracy, Perplexity, Cross-Entropy Loss

### Ablation Study 2
- **Ablated Part**: Polynomial method for attention approximation
- **Action**: REPLACE
- **Replacement**: 
  - Fourier Transform
  - Chebyshev Polynomials
- **Metrics**: Accuracy, Perplexity, Cross-Entropy Loss

</div>