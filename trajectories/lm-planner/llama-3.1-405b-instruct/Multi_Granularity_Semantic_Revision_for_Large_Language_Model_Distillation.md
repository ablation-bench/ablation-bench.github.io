<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Multi_Granularity_Semantic_Revision_for_Large_Language_Model_Distillation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Multi-Granularity Semantic Revision for Large Language Model Distillation" proposes a novel method for distilling large language models (LLMs) by revising the semantic representation at multiple levels: sequence, token, and span. The method includes a sequence correction and re-generation (SCRG) strategy, a distribution adaptive clipping Kullback-Leibler (DAC-KL) loss function, and span-level correlation consistency. The authors demonstrate the effectiveness of their approach through extensive experiments on various model families with parameters ranging from 0.1B to 13B.

Upon analyzing the paper, I suggest two missing ablation studies to further investigate the impact of the proposed method's components:

1. **Ablation of the SCRG strategy**: The SCRG strategy is a crucial component of the proposed method. An ablation study that removes or replaces SCRG with a different sequence correction approach would help understand its contribution to the overall performance.
2. **Ablation of the span-level correlation consistency**: The span-level correlation consistency component is designed to ensure consistent transfer of semantic information across related tokens. An ablation study that removes or modifies this component would help understand its impact on the model's performance.

These ablation studies would provide valuable insights into the effectiveness of the proposed method's components and help identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of SCRG strategy
- **Ablated Part**: sequence correction and re-generation strategy
- **Action**: REMOVE
- **Metrics**: ROUGE-L, Dolly Evaluation, Self-Instruct

### Ablation of span-level correlation consistency
- **Ablated Part**: span-level correlation consistency
- **Action**: REMOVE
- **Metrics**: ROUGE-L, Dolly Evaluation, Self-Instruct

</div>