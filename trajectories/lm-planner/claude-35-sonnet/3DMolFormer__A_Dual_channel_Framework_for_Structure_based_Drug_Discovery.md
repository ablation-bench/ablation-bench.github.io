<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/3DMolFormer__A_Dual_channel_Framework_for_Structure_based_Drug_Discovery

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents 3DMolFormer, a dual-channel transformer framework for both protein-ligand docking and pocket-aware 3D drug design. The authors already conducted several ablation studies:

1. Model scaling ablation (Appendix B) - testing different model sizes and architectures
2. Loss coefficient α ablation (Appendix B) - testing different weights for the composite loss
3. Pre-training ablation (Table 1) - testing model without pre-training
4. Data augmentation ablation (Table 1) - testing model without data augmentation 
5. RL fine-tuning ablation (Table 5) - testing model without RL fine-tuning

However, there are two critical components that lack ablation studies:

1. The dual-channel architecture is a key innovation but there's no ablation showing its benefits compared to single-channel alternatives. This is important since the parallel processing of discrete tokens and continuous coordinates is central to the method.

2. The coordinate normalization scheme (Eq. 1) is an important design choice for handling 3D information, but there's no ablation studying its impact or comparing different normalization approaches. The authors only briefly mention that "performance is not sensitive to the choice of q".

I believe these are the most important missing ablations that would help validate the key architectural choices of the method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Dual Channel Ablation
- **Ablated Part**: dual-channel transformer architecture
- **Action**: REPLACE
- **Replacement**: 
  - single channel with tokenized coordinates
  - single channel with continuous embeddings
- **Metrics**: %<1.0A, %<2.0A, %<3.0A, %<5.0A, Avg. RMSD, Vina Score, Vina Dock, QED, SA, Success Rate

### Coordinate Normalization Ablation
- **Ablated Part**: 3D coordinate normalization scheme
- **Action**: REPLACE
- **Replacement**: 
  - no normalization
  - min-max normalization
  - z-score normalization
- **Metrics**: %<1.0A, %<2.0A, %<3.0A, %<5.0A, Avg. RMSD, Vina Score, Vina Dock, QED, SA, Success Rate

</div>