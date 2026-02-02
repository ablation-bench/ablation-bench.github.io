<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Herald__A_Natural_Language_Annotated_Lean_4_Dataset

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Herald: A Natural Language Annotated Lean 4 Dataset" introduces a framework for translating the Mathlib4 corpus into natural language, creating the Herald dataset, and fine-tuning a model called the Herald Translator. The paper includes an ablation study on the two augmentation methods used in the dataset creation, but it does not cover all possible ablations that could provide insights into the model's performance.

One potential missing ablation study is the impact of the dependency order translation strategy. The paper mentions using Lean-Jixia to extract dependency graphs and translating statements in a level order to ensure that natural language translations of dependent theorems are available. An ablation study could investigate the effect of removing this dependency order translation strategy to understand its contribution to the model's performance.

Another missing ablation study could focus on the tactic-based augmentation strategy. The paper describes how tactic-based augmentation is used to generate additional training data by breaking down proofs into smaller steps. An ablation study could explore the impact of this augmentation strategy by removing it and observing changes in model performance. This would help determine the importance of tactic-based augmentation in improving the model's ability to translate between natural and formal languages.

Both of these ablation studies would provide valuable insights into the contributions of specific components of the methodology to the overall performance of the Herald Translator.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study on Dependency Order Translation
- **Ablated Part**: Dependency order translation strategy using Lean-Jixia
- **Action**: REMOVE
- **Metrics**: Pass@128 accuracy on miniF2F-test, accuracy on internal graduate-level textbook dataset

### Ablation Study on Tactic-Based Augmentation
- **Ablated Part**: Tactic-based augmentation strategy
- **Action**: REMOVE
- **Metrics**: Pass@128 accuracy on miniF2F-test, accuracy on internal graduate-level textbook dataset

</div>