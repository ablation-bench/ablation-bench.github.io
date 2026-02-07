<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Self_RAG__Learning_to_Retrieve__Generate__and_Critique_through_Self_Reflection

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the Self-RAG paper, I notice that while the authors conducted several ablation studies, there are still some important components that weren't fully investigated. The existing ablations mainly focused on:

1. Training ablations:
- No Retriever: Training without retrieved passages
- No Critic: Training with retrieved passages but without reflection tokens

2. Inference ablations:
- No retrieval during inference
- Hard constraints vs adaptive threshold
- Using only top 1 retrieved document
- Removing ISSUP score during beam search

However, I identify two critical missing ablation studies that could provide valuable insights:

1. The impact of different reflection token types - while the paper uses 4 types (Retrieve, ISREL, ISSUP, ISUSE), it doesn't investigate their individual contributions.

2. The effect of different critic model architectures - while they use Llama2-7B as the critic model, they don't explore how different model sizes or architectures affect the final performance.

I'll suggest these two ablations, ranked by importance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Reflection Token Type Ablation
- **Ablated Part**: Different types of reflection tokens used for self-reflection
- **Action**: REMOVE
- **Metrics**: accuracy, FactScore, citation precision, citation recall, MAUVE

### Critic Model Architecture Ablation
- **Ablated Part**: Architecture and size of the critic model
- **Action**: REPLACE
- **Replacement**: 
  - Llama2-13B
  - FLAN-T5-XL
  - T5-large
- **Metrics**: accuracy, FactScore, citation precision, citation recall, MAUVE

</div>