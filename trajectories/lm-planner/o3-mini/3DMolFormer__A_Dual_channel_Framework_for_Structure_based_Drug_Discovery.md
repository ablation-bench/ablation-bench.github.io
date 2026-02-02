<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/3DMolFormer__A_Dual_channel_Framework_for_Structure_based_Drug_Discovery

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The first proposed ablation study focuses on the method used to fuse the continuous 3D coordinate values with the token embeddings at the input stage. In 3DMolFormer, the discrete tokens (capturing atomic and SMILES information) are multiplied by their corresponding numerical (coordinate) values before entering the transformer. This multiplicative fusion is a key architectural decision in the dual-channel design. However, alternative fusion strategies (such as addition, concatenation, or a gated mechanism) might yield different representations, which can affect both docking accuracy (measured by metrics like %<2.0Å, %<3.0Å, and average RMSD) and downstream drug design performance. Testing these alternative fusion methods would clarify the contribution of the multiplicative scheme and validate that the chosen integration effectively leverages 3D structural information.

The second proposed ablation study examines the impact of freezing the docking channel weights during the reinforcement learning (RL) fine-tuning process for pocket-aware drug design. In the current method, the RL fine-tuning for generating drug candidates leverages pre-trained weights from the docking task for generating 3D coordinates by keeping them fixed. However, it remains unclear whether allowing these weights to update (or partially update) during RL fine-tuning could further improve the quality and specificity of the generated molecules. By comparing the current “frozen” approach with an alternative where the docking channel is updated end-to-end, one can assess the importance of transferring docking knowledge and how well the dual-task paradigm supports drug design. The evaluation for this ablation would use drug design metrics such as Vina Score, Vina Dock, QED, SA, and Success Rate.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Input Fusion Method Ablation
- **Ablated Part**: Fusion method of incorporating continuous 3D coordinate values with token embeddings at the input stage
- **Action**: REPLACE
- **Replacement**: 
  - addition
  - concatenation
  - gated fusion
- **Metrics**: %<2.0A, %<3.0A, Avg RMSD

### Docking Channel Weight Update Ablation in RL
- **Ablated Part**: Freezing of the docking channel weights during RL fine-tuning for pocket-aware 3D drug design
- **Action**: REPLACE
- **Replacement**: 
  - freeze docking weights
  - update all weights
- **Metrics**: Vina Score, Vina Dock, QED, SA, Success Rate

</div>