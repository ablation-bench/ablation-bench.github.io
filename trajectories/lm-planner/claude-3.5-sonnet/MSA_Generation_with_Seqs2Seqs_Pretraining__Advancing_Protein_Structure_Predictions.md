<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/MSA_Generation_with_Seqs2Seqs_Pretraining__Advancing_Protein_Structure_Predictions

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that the authors have conducted some ablation studies, particularly around:
1. Ensemble runs impact (Table 2)
2. Sequence augmentation factor (Table 3)

However, there are some critical components of the method that were not ablated and could provide important insights:

1. The most critical missing ablation is around the attention mechanisms. The paper introduces two novel attention modules - Cross-Row Attention and Cross-Column Attention - but does not evaluate their individual contributions to the model's performance.

2. Another important missing ablation is around the pretraining dataset construction. The authors use a specific approach to construct source-target pairs from MSAs (selecting 10-30 sequences for source and target), but do not evaluate how this choice impacts the model's performance.

I'll focus on suggesting ablations for the attention mechanisms since this appears to be the most critical architectural innovation in the paper and its impact is not evaluated. The dataset construction ablation would be secondary since it's more of an implementation detail.

For the attention mechanism ablation, we should test removing each type of attention separately to understand their individual contributions. The metrics should match those used in the paper - primarily LDDT and pLDDT scores on the CASP14/15 benchmarks.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Cross-Row Attention Ablation
- **Ablated Part**: Cross-Row Attention module in the decoder
- **Action**: REMOVE
- **Metrics**: LDDT, pLDDT

### Cross-Column Attention Ablation
- **Ablated Part**: Cross-Column Attention module in the decoder
- **Action**: REMOVE
- **Metrics**: LDDT, pLDDT

</div>