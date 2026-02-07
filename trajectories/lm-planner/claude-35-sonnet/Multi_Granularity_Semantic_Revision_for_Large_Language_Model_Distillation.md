<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Multi_Granularity_Semantic_Revision_for_Large_Language_Model_Distillation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that while the authors conducted several ablation studies on their multi-granularity semantic revision method, there are two important ablation studies missing that could provide valuable insights into the method's effectiveness:

1. The first missing ablation concerns the learnable sub-network in the DAC-KL loss. The authors use this sub-network to adaptively extract semantically dense areas, but they don't investigate how different architectures or removing this sub-network entirely would affect performance. This is important since the sub-network is a key component in determining which areas of the teacher's output distribution to focus on.

2. The second missing ablation relates to the span priors used for computing probability correlations. While the authors use pre-defined chunkers to extract spans, they don't investigate how different span extraction methods or span lengths affect the model's performance. This would help understand the robustness of their span-level semantic transfer approach.

The paper uses ROUGE-L as the main evaluation metric across their experiments, so I'll include this in both ablation suggestions. Additionally, since they evaluate on multiple datasets (Dolly Evaluation, Self-Instruct, Vicuna, Super-Natural, and Unnatural), these should be included in the metrics.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Sub-network Architecture Ablation
- **Ablated Part**: Learnable sub-network in DAC-KL loss
- **Action**: REPLACE
- **Replacement**: 
  - MLP with 1 hidden layer
  - MLP with 3 hidden layers
  - Linear layer only
  - No sub-network (fixed thresholds)
- **Metrics**: ROUGE-L on Dolly Evaluation, ROUGE-L on Self-Instruct, ROUGE-L on Vicuna, ROUGE-L on Super-Natural, ROUGE-L on Unnatural

### Span Extraction Method Ablation
- **Ablated Part**: Pre-defined chunker for span extraction
- **Action**: REPLACE
- **Replacement**: 
  - Fixed-length spans
  - Attention-based spans
  - Constituency parser spans
  - Random spans
- **Metrics**: ROUGE-L on Dolly Evaluation, ROUGE-L on Self-Instruct, ROUGE-L on Vicuna, ROUGE-L on Super-Natural, ROUGE-L on Unnatural

</div>