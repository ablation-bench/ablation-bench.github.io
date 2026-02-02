<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/A_Critical_Look_At_Tokenwise_Reward_Guided_Text_Generation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "A Critical Look At Tokenwise Reward-Guided Text Generation" introduces a novel approach to reward-guided text generation (RGTG) by training a Bradley-Terry reward model on partial sequences. The paper highlights the inadequacy of using full-sequence reward models for scoring partial sequences and proposes a method to address this issue. The authors conduct experiments to validate their approach, comparing it with existing methods like ARGS and CD, and demonstrate its effectiveness.

Upon reviewing the paper, it is evident that the authors have conducted several ablation studies to analyze the impact of their proposed method. However, there are still some potential areas for further investigation:

1. **Ablation of the Bradley-Terry Model**: The paper proposes using a Bradley-Terry model for training on partial sequences. An ablation study could be conducted to evaluate the impact of using different types of models for this purpose. This would help in understanding whether the choice of the Bradley-Terry model is optimal or if other models could perform better.

2. **Impact of Reward Model Size**: The paper mentions using a reward model that is significantly smaller than the base LLM. An ablation study could explore the impact of varying the size of the reward model on the performance of the RGTG method. This would provide insights into the trade-offs between computational efficiency and performance.

These ablation studies would provide a deeper understanding of the components and design choices in the proposed method, potentially leading to further improvements.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Bradley-Terry Model
- **Ablated Part**: Use of Bradley-Terry model for training on partial sequences
- **Action**: REPLACE
- **Replacement**: 
  - Logistic Regression
  - Support Vector Machine
  - Neural Network
- **Metrics**: Average Reward, Rouge-L, BLEU

### Impact of Reward Model Size
- **Ablated Part**: Size of the reward model used in RGTG
- **Action**: REPLACE
- **Replacement**: 
  - Small (e.g., 1/10th of LLM)
  - Medium (e.g., 1/5th of LLM)
  - Large (e.g., same size as LLM)
- **Metrics**: Average Reward, Rouge-L, BLEU

</div>