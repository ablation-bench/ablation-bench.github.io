<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/BetterBodies__Reinforcement_Learning_guided_Diffusion_for_Antibody_Sequence_Design

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents BetterBodies, a method that combines VAEs with offline RL guided latent diffusion for antibody sequence design. The key components are:

1. A VAE to map amino acids into a continuous latent representation
2. An offline RL policy represented by a continuous diffusion model guided by a Q-function
3. A contrastive loss to shape the VAE latent space
4. A Q-function based filtering method

Looking at the existing ablations in the paper:
- They ablate the Q-function guidance by setting η=0 (basic diffusion)
- They test different values of η to balance between basic diffusion and Q-guidance
- They evaluate the filtering method and contrastive latent space separately

Key missing ablations:
1. The choice of VAE latent space dimensionality (currently fixed at 2D) is not explored but could significantly impact performance
2. The Q-function architecture choice (currently using clipped double Q-learning) is not ablated despite being a critical component for guiding the diffusion process

I'll focus on these two as they represent core architectural choices that could significantly impact the method's performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### VAE Latent Dimension Ablation
- **Ablated Part**: VAE latent space dimensionality
- **Action**: REPLACE
- **Replacement**: 
  - 2
  - 4
  - 8
  - 16
- **Metrics**: Free Energy, Diversity, Novelty

### Q-Function Architecture Ablation
- **Ablated Part**: Q-function architecture (currently clipped double Q-learning)
- **Action**: REPLACE
- **Replacement**: 
  - Single Q-learning
  - Ensemble Q-learning (3+ networks)
  - Conservative Q-learning
- **Metrics**: Free Energy, Diversity, Novelty

</div>