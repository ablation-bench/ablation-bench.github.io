<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/CABINET__Content_Relevance_based_Noise_Reduction_for_Table_Question_Answering

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents CABINET, a framework for table QA that uses two main components:
1. Unsupervised Relevance Scorer (URS) that assigns relevance scores to table tokens
2. Weakly-supervised Parsing Statement Generator (PSG) that generates natural language descriptions of relevant rows/columns

Looking at the existing ablations in the paper:
- They ablate using URS alone vs URS+PSG
- They ablate different clustering losses for URS
- They test robustness to table perturbations
- They test with different QA LLM backbones

Key missing ablations I identify:

1. The PSG component is trained on only 300 manually annotated samples from WikiTQ dataset. There's no ablation studying how the number of training samples affects performance. This is important since manual annotation is expensive.

2. The paper combines URS and cell-based scores through linear combination (λuns and λcell) but doesn't explore other fusion strategies. Given this is a key design choice for combining the two main components, alternative fusion approaches should be studied.

I'll focus on these two as they relate to major components and design choices of the method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### PSG Training Data Size
- **Ablated Part**: number of training samples for Parsing Statement Generator
- **Action**: REPLACE
- **Replacement**: 
  - 100 samples
  - 500 samples
  - 1000 samples
- **Metrics**: Accuracy, S-BLEU

### Score Fusion Strategy
- **Ablated Part**: linear combination of URS and cell-based scores
- **Action**: REPLACE
- **Replacement**: 
  - weighted geometric mean
  - learned neural network fusion
  - max pooling
- **Metrics**: Accuracy, S-BLEU

</div>