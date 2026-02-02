<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/REPOFILTER__Adaptive_Retrieval_Context_Trimming_for_Repository_Level_Code_Completion

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "REPOFILTER: Adaptive Retrieval Context Trimming for Repository-Level Code Completion" introduces a framework that enhances code completion by filtering out irrelevant or harmful retrieved contexts. The method relies on a likelihood-based metric to evaluate the impact of each retrieved code chunk, categorizing them as positive, neutral, or negative. The REPOFILTER framework is trained to retain only the positive chunks, thereby improving completion accuracy and efficiency.

The existing ablation studies in the paper focus on the impact of different context selection strategies, such as including all retrieved chunks, only positive chunks, excluding negative chunks, and excluding neutral chunks. These studies demonstrate the effectiveness of the likelihood-based metric in identifying beneficial contexts.

However, there are potential missing ablation studies that could further elucidate the contributions of specific components of the REPOFILTER framework:

1. The impact of the likelihood-based metric thresholds (T<sub>p</sub> and T<sub>n</sub>) on the performance of REPOFILTER. The thresholds determine the categorization of chunks as positive, neutral, or negative. Ablating these thresholds could reveal their sensitivity and optimal settings for different datasets or tasks.

2. The role of adaptive-retrieval tokens (<EC> and <MC>) in the REPOFILTER framework. These tokens guide the model in deciding whether additional context is needed. An ablation study could investigate the effect of removing or altering these tokens on the model's ability to efficiently manage context retrieval and completion.

These ablation studies would provide deeper insights into the design choices of REPOFILTER and their impact on code completion performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Threshold Sensitivity Ablation
- **Ablated Part**: likelihood-based metric thresholds (T_p and T_n)
- **Action**: REPLACE
- **Replacement**: 
  - {'T_p': 5.0, 'T_n': -2.5}
  - {'T_p': 15.0, 'T_n': -7.5}
- **Metrics**: Exact Match (EM), Edit Similarity (ES)

### Adaptive-Retrieval Token Ablation
- **Ablated Part**: adaptive-retrieval tokens (<EC> and <MC>)
- **Action**: REMOVE
- **Metrics**: Exact Match (EM), Edit Similarity (ES)

</div>