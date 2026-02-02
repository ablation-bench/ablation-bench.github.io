<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/curriculum_learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "On Curriculum Learning for Commonsense Reasoning" explores the impact of curriculum learning on finetuning pretrained language models for commonsense reasoning tasks. The study introduces a human-like easy-to-difficult curriculum and an adaptive curriculum that updates data ranking based on the learner model's state. The paper uses three difficulty measures: question answering probability, variability, and out-of-distribution scores. The experiments are conducted on five commonsense reasoning tasks, showing significant performance improvements.

To design ablation studies, we should focus on the key components of the curriculum learning approach: the fixed and adaptive curriculum strategies, the difficulty scoring functions, and the pacing function parameters. These components are crucial to understanding the contribution of each part to the overall performance improvement.

1. **Fixed vs. Adaptive Curriculum**: An ablation study could involve removing the adaptive component to assess the impact of dynamic data ranking updates.

2. **Difficulty Scoring Functions**: The paper uses three different scoring functions. Ablating one or more of these could reveal their individual contributions.

3. **Pacing Function Parameters**: The pacing function has several parameters (starting percentage, increase factor, step length). Ablating or altering these parameters could help understand their role in the curriculum's effectiveness.

4. **Reverse Curriculum Order**: The paper mentions reversing the curriculum order to difficult-to-easy in adaptive learning. An ablation study could test the impact of this reversal.

5. **Teacher Model's Role**: The teacher model is used to rank data. An ablation study could explore the effect of using a different model or no model for ranking.

These ablation studies will help attribute the performance improvements to specific components of the curriculum learning approach.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Fixed vs. Adaptive Curriculum
- **Ablated Part**: Adaptive curriculum component
- **Action**: REMOVE
- **Metrics**: accuracy, F1-score, generalization to unseen data

### Ablation 2: Difficulty Scoring Functions
- **Ablated Part**: Variability scoring function
- **Action**: REMOVE
- **Metrics**: accuracy, F1-score, generalization to unseen data

### Ablation 3: Pacing Function Parameters
- **Ablated Part**: Pacing function parameters
- **Action**: REPLACE
- **Replacement**: 
  - {'starting_percentage': 0.1, 'increase_factor': 1.5, 'step_length': 10}
  - {'starting_percentage': 0.2, 'increase_factor': 2.0, 'step_length': 5}
- **Metrics**: accuracy, F1-score, generalization to unseen data

### Ablation 4: Reverse Curriculum Order
- **Ablated Part**: Reverse curriculum order in adaptive learning
- **Action**: REMOVE
- **Metrics**: accuracy, F1-score, generalization to unseen data

### Ablation 5: Teacher Model's Role
- **Ablated Part**: Teacher model for data ranking
- **Action**: REPLACE
- **Replacement**: 
  - random ranking
  - pretrained model with different architecture
- **Metrics**: accuracy, F1-score, generalization to unseen data

</div>