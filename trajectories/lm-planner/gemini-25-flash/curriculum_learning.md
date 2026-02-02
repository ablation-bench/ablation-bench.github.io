<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/curriculum_learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants a list of up to 5 important ablation studies for the paper "On Curriculum Learning for Commonsense Reasoning". I need to identify the core components of their proposed method and suggest ablations, ranking them by importance.

The key components are:
1.  **Curriculum Learning (CL)**: Ordering data (easy-to-difficult or difficult-to-easy) instead of random.
2.  **Fixed Curriculum Learning (FCL)**: Static ranking based on an initial teacher model.
3.  **Adaptive Curriculum Learning (ACL)**: Dynamic ranking updated based on the learner model.
4.  **Difficulty Scoring Functions**: QAP, Variability, Energy.
5.  **Ranking Direction**: Easy-to-difficult (FCL), difficult-to-easy (ACL after initial ranking).
6.  **Pacing Function**: Controls the rate of introducing difficult samples in FCL.

Based on these components, I will propose the following ablation studies, ranked by importance:

1.  **Random Data Order Baseline**: This is the most fundamental comparison. The paper's core claim is that CL improves performance over random ordering. An ablation study explicitly comparing their best CL method (or both FCL and ACL) against the standard random order baseline is essential to quantify the overall benefit of using *any* curriculum.
2.  **Difficulty Scoring Function Comparison**: The paper explores three different ways to measure difficulty (QAP, Variability, Energy). An ablation study comparing the performance when using each of these scoring functions is crucial to understand which method is most effective for ranking data in this context and why.
3.  **Fixed vs. Adaptive Curriculum**: The paper proposes both FCL and ACL. An ablation study comparing these two approaches directly helps determine the added value of the adaptive mechanism over a fixed curriculum.
4.  **ACL Ranking Direction**: In Adaptive CL, the paper mentions flipping the ranking to difficult-to-easy to reinforce learning from hard samples. An ablation study comparing this difficult-to-easy approach in ACL against an easy-to-difficult approach throughout ACL would investigate the impact of this specific design choice.

These four ablations cover the main variations and comparisons presented or implied in the paper's method and results. They are ranked from the most general validation of CL itself to more specific aspects of the proposed CL variants.

The paper uses performance metrics on five commonsense reasoning tasks. Accuracy is a standard metric for these types of tasks (multiple-choice QA, NLI, etc.), and the abstract refers to "significant improvements in performance". I will use "Accuracy" as the metric for all ablations, assuming it's the primary evaluation metric used across the tasks.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Random Data Order Baseline
- **Ablated Part**: Curriculum-based data ordering
- **Action**: REPLACE
- **Replacement**: 
  - Random data order
- **Metrics**: Accuracy

### Difficulty Scoring Function Comparison
- **Ablated Part**: Method for scoring sample difficulty
- **Action**: REPLACE
- **Replacement**: 
  - Question Answering Probability
  - Model Variability
  - Energy
- **Metrics**: Accuracy

### Fixed vs. Adaptive Curriculum
- **Ablated Part**: Adaptive mechanism in Curriculum Learning
- **Action**: REMOVE
- **Metrics**: Accuracy

### ACL Ranking Direction
- **Ablated Part**: Ranking direction in Adaptive Curriculum Learning
- **Action**: REPLACE
- **Replacement**: 
  - Easy-to-difficult ranking throughout ACL
- **Metrics**: Accuracy

</div>