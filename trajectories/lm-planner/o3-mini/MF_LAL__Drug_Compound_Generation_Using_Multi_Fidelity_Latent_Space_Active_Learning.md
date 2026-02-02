<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/MF_LAL__Drug_Compound_Generation_Using_Multi_Fidelity_Latent_Space_Active_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper includes thorough ablations on the contribution of each fidelity level (e.g., removing individual fidelities), the role of the likelihood term in the generation objective, and comparisons of different encoder/decoder architectures (fully-connected vs. Transformer vs. GCN). However, two important aspects remain unexplored. First, while the work stresses the benefits of its novel Bayesian active learning algorithm, it does not include an ablation that compares its active learning query strategy (using an upper confidence bound and uncertainty thresholds) against a baseline where queries are selected randomly. Evaluating this would provide insight into the efficiency gains from active learning versus passive (random) query selection in building the multi-fidelity dataset and improving compound quality. Second, the method’s key innovation involves a hierarchical latent space where inter-fidelity linking networks (the h networks) pass information from lower to higher fidelities. An ablation that removes these linking networks—by, for example, using a shared latent representation or bypassing the transformation—would reveal how critical the sequential information passing is to achieving improved surrogate modeling performance and generation quality.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Active Learning Query Strategy
- **Ablated Part**: Active learning-based query generation using UCB acquisition with uncertainty thresholds
- **Action**: REPLACE
- **Replacement**: 
  - Random sampling
  - Uniform query selection
- **Metrics**: Mean ABFE, Top 3 ABFE scores

### Ablation: Inter-Fidelity Linking Networks
- **Ablated Part**: Hierarchical latent space information passing via the h networks between fidelity levels
- **Action**: REMOVE
- **Metrics**: Mean ABFE, Reconstruction Accuracy, Top 3 ABFE scores

</div>