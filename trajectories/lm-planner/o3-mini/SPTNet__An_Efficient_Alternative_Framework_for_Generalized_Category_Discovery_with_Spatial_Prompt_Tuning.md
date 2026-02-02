<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/SPTNet__An_Efficient_Alternative_Framework_for_Generalized_Category_Discovery_with_Spatial_Prompt_Tuning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One important component of SPTNet is the careful optimization of the spatial prompts P^s. In the paper the authors set the weight decay for P^s to zero in order to preserve the diversity of the learned prompts. However, no ablation is shown to quantify the impact of this design choice. Varying the weight decay (e.g., using a small nonzero value) could reveal the sensitivity of SPTNet to regularization on prompt parameters, indicating if a nonzero weight decay might hurt or help the model’s generalization on seen and unseen classes. Another aspect that is not ablated is the initialization strategy for the spatial prompts. The performance of learned parameters—especially in a delicate two‐stage (alternating) training framework—may be significantly influenced by how they are initialized (e.g., random normal, uniform, or even zero initialization). Thus, proposing an ablation study on different initialization schemes can shed light on the stability and convergence of the learned spatial prompts in SPTNet.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Weight Decay for Spatial Prompts
- **Ablated Part**: Regularization of the learnable spatial prompt parameters (P^s) via weight decay
- **Action**: REPLACE
- **Replacement**: 
  - 0
  - 0.0001
  - 0.0005
  - 0.001
- **Metrics**: ACC_All, ACC_Old, ACC_New

### Ablation: Prompt Initialization for Spatial Prompts
- **Ablated Part**: Initialization strategy for the spatial prompt parameters (P^s)
- **Action**: REPLACE
- **Replacement**: 
  - random_normal
  - uniform
  - zero
- **Metrics**: ACC_All, ACC_Old, ACC_New

</div>