<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Self_RAG__Learning_to_Retrieve__Generate__and_Critique_through_Self_Reflection

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One key novelty of SELF-RAG is its integrated self-reflection mechanism, where the model interleaves generated output with reflection tokens to decide whether to retrieve information, and to evaluate its own output. While the paper provides ablations such as “No Retriever,” “No Critic,” and variations in beam search (e.g., “Remove <I>SSUP”, “Hard constraints”, “Retrieve top 1”), it does not investigate how the granularity or frequency of self-reflection might affect generation quality and factuality.

A first missing ablation study is to vary the segmentation unit at which reflection tokens are inserted. In the paper, one sentence is treated as a segment, but the design might be sensitive to this choice. For example, inserting reflection tokens at a paragraph-level (or even sub-sentence-level) might alter the trade-off between detailed self-assessment and runtime efficiency, ultimately impacting metrics such as factuality (FactScore), citation precision and recall, and fluency (MAUVE). An ablation varying these segmentation choices would help understand the sensitivity of the method to the definition of a "segment."

A second important missing ablation is to examine the frequency at which self-reflection tokens are generated. Currently, SELF-RAG interleaves reflection tokens at every segment. However, it is unclear whether such fine-grained self-reflection is always necessary. An investigation comparing the baseline (reflection tokens after every segment) with variants that generate reflection tokens less frequently (for example, after every 2 segments or only at the end) would provide useful insights into the trade-off between retrieval/correction benefits and potential downsides (e.g., higher complexity or disruption of fluency). Metrics for this ablation would include factual accuracy (FactScore), citation precision, overall fluency (MAUVE), and generation coherence.

These two ablations are critical as they scrutinize the core self-reflection mechanism of SELF-RAG, which distinguishes it from standard RAG methods.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Segment Granularity Ablation
- **Ablated Part**: The unit of segmentation used for interleaving self-reflection tokens (e.g., sentence-level vs. paragraph-level vs. sub-sentence-level) in SELF-RAG training and inference.
- **Action**: REPLACE
- **Replacement**: 
  - sentence-level
  - paragraph-level
  - sub-sentence-level
- **Metrics**: FactScore, citation precision, MAUVE

### Reflection Token Frequency Ablation
- **Ablated Part**: The frequency at which self-reflection tokens are inserted during generation (e.g., after every segment vs. after every two segments vs. only at end-of-generation) in SELF-RAG.
- **Action**: REPLACE
- **Replacement**: 
  - every segment
  - every two segments
  - end-of-generation only
- **Metrics**: FactScore, citation precision, MAUVE, fluency

</div>