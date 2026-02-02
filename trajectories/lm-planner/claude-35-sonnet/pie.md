<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/pie

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, the main components that contribute to the performance are:

1. The adaptation strategies for code optimization, including:
   - Few-shot prompting with different variants
   - Retrieval-based prompting
   - Performance-conditioned generation
   - Synthetic data augmentation via self-play

2. The key metrics used in the paper are:
   - Mean speedup over baseline
   - Percentage of test set optimized by at least 10%

Looking at these components, I suggest the following ablation studies ranked by importance:

1. Test the impact of performance-conditioning by removing the performance tags
2. Evaluate the contribution of synthetic data augmentation
3. Compare different retrieval mechanisms in the retrieval-based prompting
4. Test different numbers of examples in few-shot prompting
5. Evaluate the impact of chain-of-thought prompting

These ablations would help isolate the contribution of each major component while using the same metrics as the paper.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Performance Conditioning Ablation
- **Ablated Part**: Performance tags during training and inference
- **Action**: REMOVE
- **Metrics**: mean_speedup, percent_optimized_10

### Synthetic Data Ablation
- **Ablated Part**: Synthetic data augmentation from self-play
- **Action**: REMOVE
- **Metrics**: mean_speedup, percent_optimized_10

### Retrieval Mechanism Ablation
- **Ablated Part**: CodeBertScore embedding for retrieval
- **Action**: REPLACE
- **Replacement**: 
  - random retrieval
  - keyword-based retrieval
  - syntax-based retrieval
- **Metrics**: mean_speedup, percent_optimized_10

### Few-Shot Examples Ablation
- **Ablated Part**: Number of few-shot examples
- **Action**: REPLACE
- **Replacement**: 
  - 0 examples
  - 1 example
  - 4 examples
  - 8 examples
- **Metrics**: mean_speedup, percent_optimized_10

### Chain-of-Thought Ablation
- **Ablated Part**: Chain-of-thought prompting
- **Action**: REMOVE
- **Metrics**: mean_speedup, percent_optimized_10

</div>