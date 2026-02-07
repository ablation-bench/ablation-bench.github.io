<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Revisiting_Convolution_Architecture_in_the_Realm_of_DNA_Foundation_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that the authors have already conducted several ablation studies, particularly on:
1. The gating mechanism and dual-branch structure (Section 4.5)
2. The dilation vs downsampling comparison (Section 4.4)
3. The kernel size and dilation rate variations (Section A.3.2)

However, there are two important missing ablation studies that could provide valuable insights:

1. The most critical missing ablation is on the pretraining strategy. While the paper mentions using MLM pretraining with 10% masking rate, there's no ablation studying how different masking rates or pretraining objectives affect the model's performance. This is particularly important given that pretraining is a crucial component of foundation models.

2. The second important missing ablation is on the input representation. The paper mentions using character-level tokenization but doesn't investigate how different input representations (e.g., k-mer tokenization, one-hot encoding) affect the model's performance. This is especially relevant given that other DNA language models use different tokenization strategies.

I'll focus on these two ablations as they represent core design choices that weren't thoroughly investigated in the paper.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Pretraining Strategy Ablation
- **Ablated Part**: MLM pretraining masking rate and objective
- **Action**: REPLACE
- **Replacement**: 
  - 5% masking rate
  - 15% masking rate
  - 20% masking rate
  - next nucleotide prediction objective
- **Metrics**: AUC score, MCC score, F1 score

### Input Representation Ablation
- **Ablated Part**: character-level tokenization
- **Action**: REPLACE
- **Replacement**: 
  - k-mer tokenization (k=3)
  - k-mer tokenization (k=6)
  - one-hot encoding
- **Metrics**: AUC score, MCC score, F1 score

</div>