<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/BetterBodies__Reinforcement_Learning_guided_Diffusion_for_Antibody_Sequence_Design

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "BetterBodies: Reinforcement Learning guided Diffusion for Antibody Sequence Design" proposes a novel method combining VAEs, latent diffusion, and offline RL for generating antibody sequences. The core components include a VAE to map discrete amino acids to a continuous latent space, a continuous diffusion model operating in this latent space, an offline RL Q-function to guide the diffusion process, a stepwise generation approach, a contrastive loss for the VAE to incorporate biophysical properties, and a Q-function based filtering step.

The paper presents several ablation studies:
1.  **Effect of RL Guidance (η):** Section 6.1 investigates the impact of the hyperparameter η, which balances the behavior cloning loss (diffusion towards the data distribution) and the Q-function maximization loss (guidance towards high-affinity sequences). Setting η=0 corresponds to basic diffusion without RL guidance. This is a crucial ablation demonstrating the value of the RL guidance.
2.  **Effect of Q-function Filtering:** Section 6.2 compares the performance of BetterBodies (with η=24) against BetterBodies-F, which adds the Q-function based filtering step. This shows the contribution of the filtering mechanism.
3.  **Effect of Contrastive Latent:** Section 6.2 also compares BetterBodies-F against BetterBodies-CF, which incorporates the contrastive loss during VAE training in addition to filtering. Figure 4 visualizes the effect of the contrastive loss on the VAE latent space. This demonstrates the benefit of shaping the latent space using biophysical properties.

While these ablations cover important aspects like the guidance strength, filtering, and the contrastive VAE, they do not fully explore other fundamental design choices. Two significant missing ablations are related to the VAE configuration and the state representation in the stepwise generation process.

Firstly, the VAE is essential for enabling continuous diffusion on discrete amino acids. The paper uses a 2D latent space (L259-260), but the choice of dimensionality is not justified or ablated. The performance of the diffusion model and the RL guidance could be sensitive to the properties of this latent space, including its dimension. An ablation varying the latent space dimensionality would assess its impact and potentially identify an optimal size.

Secondly, the method employs a stepwise generation process, building the sequence one amino acid at a time, conditioned on the sequence generated so far (L140-141, L213-215). The state 's' representing the sequence generated thus far is encoded using concatenated one-hot vectors (L746-749). The paper mentions that other representations, such as concatenated VAE latent vectors, could also be used (L746-749). Ablating this state representation choice would investigate whether using the VAE's continuous, potentially property-aware, representation of the sequence history improves performance compared to the simpler one-hot encoding. This directly tests a design choice within the stepwise generation framework.

These two ablations are important because they probe the impact of the VAE's configuration, which is foundational to the latent diffusion approach, and the state representation within the stepwise generation, which is a key structural choice of the method. Evaluating these would provide deeper insights into the contributions of these specific design decisions to BetterBodies' performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### VAE Latent Dimension Ablation
- **Ablated Part**: Dimensionality of the VAE latent space for amino acid representation
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 4
  - 8
- **Metrics**: Free Energy, Diversity, Novelty

### State Representation Ablation
- **Ablated Part**: Representation of the sequence generated so far (state 's') for the diffusion policy and Q-function
- **Action**: REPLACE
- **Replacement**: 
  - Concatenated One-Hot Encoding
  - Concatenated VAE Latent Vectors
- **Metrics**: Free Energy, Diversity, Novelty

</div>