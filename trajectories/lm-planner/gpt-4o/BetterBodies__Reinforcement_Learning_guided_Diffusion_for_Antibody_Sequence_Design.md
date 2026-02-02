<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/BetterBodies__Reinforcement_Learning_guided_Diffusion_for_Antibody_Sequence_Design

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "BetterBodies: Reinforcement Learning guided Diffusion for Antibody Sequence Design" presents a novel method that combines Variational Autoencoders (VAEs) with offline Reinforcement Learning (RL) guided latent diffusion to generate antibody sequences with improved binding affinity. The method incorporates several components, including a VAE for encoding amino acids into a latent space, a diffusion model guided by a learned Q-function, and a contrastive loss to reflect biophysical properties in the latent space. The paper evaluates the method using metrics such as free energy, diversity, and novelty of generated sequences.

The existing ablation studies in the paper focus on the effect of Q-function guidance on diffusion, the balance between basic diffusion and Q-guidance, and the impact of filtering and contrastive latent methods. However, there are some missing ablation studies that could provide further insights into the contributions of specific components of the method.

One missing ablation study could involve the removal of the contrastive loss used to shape the VAE latent space. This would help to understand the impact of encoding biophysical properties on the performance of the generated sequences. Another potential ablation study could involve replacing the Q-function-based filtering with alternative filtering methods to assess the effectiveness of the Q-function in enhancing sequence affinity.

These ablation studies would provide a deeper understanding of the contributions of the contrastive loss and Q-function-based filtering to the overall performance of the BetterBodies method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Contrastive Loss
- **Ablated Part**: Contrastive loss used to shape the VAE latent space
- **Action**: REMOVE
- **Metrics**: free_energy, diversity, novelty

### Alternative Filtering Methods
- **Ablated Part**: Q-function-based filtering
- **Action**: REPLACE
- **Replacement**: 
  - random filtering
  - threshold-based filtering
- **Metrics**: free_energy, diversity, novelty

</div>