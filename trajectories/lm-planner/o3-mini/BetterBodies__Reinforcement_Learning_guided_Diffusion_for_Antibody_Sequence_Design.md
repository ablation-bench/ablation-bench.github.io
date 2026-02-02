<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/BetterBodies__Reinforcement_Learning_guided_Diffusion_for_Antibody_Sequence_Design

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper already presents several ablations, including experiments varying the Q-guidance strength (η) and evaluating variations with filtering and contrastive loss to shape the VAE latent space. However, it leaves out evaluations of two components that are central to the method. First, the paper uses a pre-trained VAE to encode discrete amino acids as two-dimensional continuous latent vectors and then freezes it during diffusion training. It would be important to study whether this specific form of representation is crucial for performance. An ablation study replacing the fixed VAE representation with an alternative (for example, one-hot state representations or jointly training the VAE with the diffusion model) would help to attribute performance improvements to the biophysically-informed continuous representation versus a more straightforward discrete representation. Second, the method applies a Q-function based filtering strategy that selects generated sequences using a fixed threshold (50th percentile) based on predicted affinity. It remains unclear how sensitive the performance is to the choice of this filtering threshold. An ablation study that explores different filtering thresholds (e.g., 25th, 50th, or 75th percentile) would offer insights on the tradeoffs between affinity improvement and the diversity/novelty of generated sequences.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### VAE Representation Ablation
- **Ablated Part**: The use of a pre-trained and frozen VAE for continuous amino acid representation in the diffusion process
- **Action**: REPLACE
- **Replacement**: 
  - Use one-hot encoding for state and action representation
  - Jointly train the VAE with the diffusion model instead of freezing it
- **Metrics**: Free Energy, Diversity, Novelty, Training Stability

### Filtering Threshold Sensitivity
- **Ablated Part**: The fixed Q-function based filtering mechanism using a 50th percentile threshold for sequence selection
- **Action**: REPLACE
- **Replacement**: 
  - 25th percentile cutoff
  - 50th percentile cutoff
  - 75th percentile cutoff
- **Metrics**: Free Energy, Diversity, Novelty

</div>