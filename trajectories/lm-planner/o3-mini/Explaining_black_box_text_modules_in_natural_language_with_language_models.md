<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Explaining_black_box_text_modules_in_natural_language_with_language_models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After reviewing the paper, we noticed that while the authors extensively vary key hyperparameters (such as ngram order, underlying corpus, and helper LLM choice) and even compare to a baseline without synthetic scoring, they do not examine how two important subcomponents affect overall performance. First, although the candidate explanation generation step selects 30 random ngrams from the top 50, the sampling strategy itself (e.g. the effect of using a deterministic top‐k versus random sampling or varying the number of ngrams) is not ablated. Such an ablation would help determine whether the randomness or the fixed number of ngrams plays a critical role in the quality and reliability of the explanation candidate. Second, in the synthetic scoring step the method generates an equal number of “positive” (explanation‐related) and “negative” (unrelated) synthetic texts. However, the impact of altering this ratio is not examined. Modifying the proportion of positive versus negative synthetic texts could significantly affect the explanation score computation and ultimately the selection of the top explanation. The following two proposed ablation studies are ranked by their importance in understanding these critical design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Candidate Ngram Sampling Strategy
- **Ablated Part**: The candidate explanation generation step, specifically the strategy for selecting ngrams (i.e. random selection of 30 from top 50)
- **Action**: REPLACE
- **Replacement**: 
  - deterministic selection with fixed top-30 ngrams
  - deterministic selection with top-50 ngrams
  - random sampling with different k values (e.g. k=10, k=30, k=50)
- **Metrics**: Accuracy, BERT Score, Explanation Score

### Ablation on Synthetic Sample Ratio
- **Ablated Part**: The synthetic scoring step’s ratio of positive (explanation-related) to negative (unrelated) synthetic texts
- **Action**: REPLACE
- **Replacement**: 
  - 1:1 ratio (baseline: 10 positive, 10 negative)
  - 2:1 ratio (e.g. 14 positive, 6 negative)
  - 1:2 ratio (e.g. 6 positive, 14 negative)
- **Metrics**: Accuracy, BERT Score, Explanation Score

</div>