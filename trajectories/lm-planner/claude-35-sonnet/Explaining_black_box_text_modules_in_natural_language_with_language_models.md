<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Explaining_black_box_text_modules_in_natural_language_with_language_models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that the SASC method has two main components:
1. Summarization step: using a helper LLM (GPT-3) to summarize top ngrams into candidate explanations
2. Synthetic scoring step: using the helper LLM to generate synthetic text and evaluate explanations

The paper already includes some ablations in Table 2, testing:
- Different ngram sizes (bigrams vs trigrams vs 4-grams)
- Different helper LLMs (GPT-3 vs LLaMA-2) for summarization and generation

However, I identify two important missing ablations:

1. The method of selecting top ngrams for summarization. Currently they "select a random subset of the top ngrams" (30 random ngrams from top 50). This selection strategy could significantly impact the quality of explanations.

2. The number of synthetic examples generated for scoring. Currently they generate "20 synthetic strings for each candidate explanation". The number of examples could affect the reliability of the explanation scores.

These components are critical to the method's performance but weren't systematically evaluated.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ngram Selection Strategy Ablation
- **Ablated Part**: Random selection of top ngrams for summarization
- **Action**: REPLACE
- **Replacement**: 
  - select top-k ngrams deterministically
  - select ngrams weighted by their module response
  - select ngrams clustered by similarity
- **Metrics**: Accuracy, BERT Score

### Synthetic Examples Size Ablation
- **Ablated Part**: Number of synthetic examples for scoring explanations
- **Action**: REPLACE
- **Replacement**: 
  - 10 examples
  - 50 examples
  - 100 examples
- **Metrics**: Accuracy, BERT Score, Explanation score

</div>