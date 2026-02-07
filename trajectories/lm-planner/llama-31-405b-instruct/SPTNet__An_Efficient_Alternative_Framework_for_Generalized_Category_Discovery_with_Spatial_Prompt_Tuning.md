<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/SPTNet__An_Efficient_Alternative_Framework_for_Generalized_Category_Discovery_with_Spatial_Prompt_Tuning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a novel method for Generalized Category Discovery (GCD) called SPTNet, which uses a two-stage iterative learning framework to optimize both model parameters and data parameters. The method introduces a new spatial prompt tuning method (SPT) that considers the spatial property of image data, enabling the model to better focus on object parts that can transfer between seen and unseen classes. The paper presents extensive experiments on various datasets, demonstrating the effectiveness of SPTNet in outperforming existing GCD methods.

To further analyze the method, we suggest two missing ablation studies:

1. **Effect of spatial prompt size on different datasets**: The paper only presents the effect of spatial prompt size on the CUB dataset. It would be interesting to see how the spatial prompt size affects the performance on other datasets, such as ImageNet-100 and Stanford Cars.
2. **Comparison of different prompt initialization methods**: The paper uses a random initialization method for the prompts. It would be useful to compare the performance of SPTNet with different prompt initialization methods, such as using pre-trained language models or other initialization techniques.

These ablation studies can provide further insights into the effectiveness of SPTNet and help identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: spatial prompt size
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 5
  - 10
  - 20
  - 30
- **Metrics**: accuracy

### Ablation B
- **Ablated Part**: prompt initialization method
- **Action**: REPLACE
- **Replacement**: 
  - random
  - pre-trained language model
  - other initialization techniques
- **Metrics**: accuracy

</div>