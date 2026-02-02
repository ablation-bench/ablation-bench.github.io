<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/pie

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies to isolate the contribution of each major component in adapting LLMs for performance optimization. First, we remove the performance-conditioned generation mechanism (i.e. the use of performance tags during fine-tuning) to quantify its impact on the produced speedup and optimization coverage. Second, we remove the synthetic data augmentation created via self-play to assess whether including additional synthetic examples significantly boosts performance. Third, we replace the dynamic retrieval‐based few‐shot prompting with simpler alternatives (e.g. random or static few‐shot examples) to evaluate how critical the retrieval component is for constructing informative prompts. Fourth, we remove the chain-of-thought (CoT) instructions from the prompting procedure; this ablation helps us understand whether encouraging the LLM to “think” explicitly contributes to the final speedup. Finally, we investigate the effect of data quality by replacing the filtered high-quality slow–fast pairs with the full unfiltered dataset (or alternative filtering thresholds) during fine-tuning. For all studies, we propose to evaluate traditional performance metrics such as mean speedup, optimization coverage (e.g. percentage of programs with at least a 10% improvement), and unit test pass rate to ensure correctness.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Performance-Conditioned Fine-Tuning
- **Ablated Part**: Performance-conditioned generation via performance tags during fine-tuning
- **Action**: REMOVE
- **Metrics**: mean speedup, optimization coverage (%), unit test pass rate

### Ablation: Synthetic Data Augmentation
- **Ablated Part**: Synthetic data augmentation using self-play generated examples
- **Action**: REMOVE
- **Metrics**: mean speedup, optimization coverage (%), unit test pass rate

### Ablation: Retrieval-Based Few-Shot Prompting
- **Ablated Part**: Dynamic retrieval-based few-shot prompting component
- **Action**: REPLACE
- **Replacement**: 
  - Randomly sampled few-shot examples
  - Static few-shot prompts
- **Metrics**: mean speedup, optimization coverage (%), unit test pass rate

### Ablation: Chain-of-Thought Prompting
- **Ablated Part**: Chain-of-thought (CoT) reasoning instructions in the prompting process
- **Action**: REMOVE
- **Metrics**: mean speedup, optimization coverage (%), unit test pass rate

### Ablation: Data Quality Filtering
- **Ablated Part**: High-quality data filtering (using a curated subset of slow-fast pairs) for fine-tuning
- **Action**: REPLACE
- **Replacement**: 
  - Full dataset without filtering
  - Alternative filtering thresholds
- **Metrics**: mean speedup, optimization coverage (%), unit test pass rate

</div>