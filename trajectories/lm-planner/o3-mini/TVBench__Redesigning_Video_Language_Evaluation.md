<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/TVBench__Redesigning_Video_Language_Evaluation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The first missing ablation focuses on the design of the QA templates. TVBench intentionally uses task-specific, minimally informative templates to minimize textual bias and force models to rely on the video content. However, the paper does not evaluate how much this careful template design itself contributes to the benchmark’s effectiveness. An ablation study could replace these rigorously designed templates with alternative, more verbose or overly informative QA pairs (e.g., using LLM-generated or MVBench-style QA pairs) to quantify the impact on performance. The changes in accuracy and the gap between text-only and video-based performance would reveal the extent of textual bias that re-emerges when using less controlled templates.

The second missing ablation targets the role of temporal context length. Although TVBench is built to demand temporal reasoning, the paper does not systematically investigate how varying the temporal span (i.e., the number of frames or duration of video provided) affects model performance. This ablation would involve gradually reducing the temporal context (for example to 25%, 50%, and 75% of the full video) and measuring the accuracy drop on the temporal reasoning tasks. Such an experiment would directly demonstrate the sensitivity of video-language models to the amount of temporal information provided.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### QA Template Informativeness Ablation
- **Ablated Part**: Task-specific QA templates designed to reduce textual bias
- **Action**: REPLACE
- **Replacement**: 
  - LLM-generated verbose QA pairs
  - Generic, overly informative QA templates
  - Original MVBench QA pairs
- **Metrics**: accuracy, text-vs-video performance gap

### Temporal Context Length Ablation
- **Ablated Part**: Temporal information provided via the video input (i.e., number of frames/clip duration)
- **Action**: REPLACE
- **Replacement**: 
  - 25% of video frames
  - 50% of video frames
  - 75% of video frames
  - 100% of video frames
- **Metrics**: accuracy, temporal reasoning performance

</div>