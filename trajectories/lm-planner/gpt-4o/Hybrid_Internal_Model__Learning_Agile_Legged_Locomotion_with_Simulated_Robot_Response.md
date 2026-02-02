<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Hybrid_Internal_Model__Learning_Agile_Legged_Locomotion_with_Simulated_Robot_Response

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Hybrid Internal Model: Learning Agile Legged Locomotion with Simulated Robot Response" introduces a novel approach to estimating external disturbances in legged robots using a Hybrid Internal Model (HIM). The method leverages contrastive learning to optimize a hybrid internal embedding, which includes both explicit velocity and implicit stability representations. The paper already includes several ablation studies, such as removing velocity input, removing velocity loss, removing internal latent input, and removing internal latent loss. These studies aim to understand the contribution of different components of the HIM framework.

However, there are still some potential areas for further ablation studies that could provide additional insights into the method's performance. One such area is the contrastive learning component, which is crucial for optimizing the hybrid internal embedding. Another area is the batch-level information exploitation, which is claimed to improve robustness to noise and sample efficiency.

1. **Contrastive Learning Component**: The paper uses contrastive learning to optimize the hybrid internal embedding. An ablation study could investigate the impact of this component by replacing it with other representation learning techniques, such as regression or autoencoders. This would help to understand the specific benefits of using contrastive learning in this context.

2. **Batch-Level Information Exploitation**: The paper claims that exploiting batch-level information improves robustness to noise and sample efficiency. An ablation study could explore the impact of this by removing or altering the batch-level information processing. This would help to quantify the contribution of batch-level information to the overall performance of the method.

These ablation studies would provide a deeper understanding of the critical components of the HIM framework and their contributions to the method's success.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Contrastive Learning
- **Ablated Part**: Contrastive learning component used for optimizing the hybrid internal embedding
- **Action**: REPLACE
- **Replacement**: 
  - Regression
  - Autoencoder
- **Metrics**: Normalized Linear Velocity Tracking Score, Normalized Angular Velocity Tracking Score, Maximum Reachable Terrain Level

### Ablation on Batch-Level Information
- **Ablated Part**: Batch-level information exploitation
- **Action**: REMOVE
- **Metrics**: Normalized Linear Velocity Tracking Score, Normalized Angular Velocity Tracking Score, Maximum Reachable Terrain Level

</div>