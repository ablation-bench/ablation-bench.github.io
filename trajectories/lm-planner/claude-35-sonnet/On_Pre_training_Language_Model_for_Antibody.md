<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/On_Pre_training_Language_Model_for_Antibody

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that while the authors conducted several experiments comparing different models and architectures, there are some important ablations missing that could provide deeper insights into the method's effectiveness:

1. The paper introduces two key evolution-aware pretraining objectives - Ancestor Germline Prediction (AGP) and Mutation Position Prediction (MPP). While they do ablate these components individually, they don't investigate the impact of different sampling strategies for the AGP task. Currently, they use a fixed probability p=0.3 for substituting paired germlines with random ones.

2. The paper uses a concatenation approach with [SEP] token to combine antibody and germline sequences. This architectural choice is important but not ablated. Alternative approaches like using two separate encoders or different special tokens could impact performance.

These missing ablations are important because:
- The AGP sampling strategy directly affects how the model learns evolutionary relationships
- The sequence concatenation approach is fundamental to how the model processes paired sequences
- Both aspects are core to the method's novelty in incorporating evolutionary information

Looking at the existing ablations in the paper:
- They already ablate AGP and MPP objectives individually 
- They compare different model sizes
- They evaluate different pre-training approaches

Therefore, I'll suggest the two most important missing ablations that could provide additional insights into the method's key components.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### AGP Sampling Strategy Ablation
- **Ablated Part**: Probability of substituting paired germlines with random ones in AGP objective
- **Action**: REPLACE
- **Replacement**: 
  - 0.1
  - 0.5
  - 0.7
- **Metrics**: AUC, F1, MCC

### Sequence Pairing Architecture Ablation
- **Ablated Part**: Concatenation with [SEP] token approach for combining antibody and germline sequences
- **Action**: REPLACE
- **Replacement**: 
  - dual encoder with cross-attention
  - parallel encoders with late fusion
- **Metrics**: AUC, F1, MCC

</div>