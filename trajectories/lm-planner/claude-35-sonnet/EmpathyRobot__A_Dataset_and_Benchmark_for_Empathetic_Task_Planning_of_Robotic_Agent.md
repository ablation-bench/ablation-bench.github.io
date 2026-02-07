<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/EmpathyRobot__A_Dataset_and_Benchmark_for_Empathetic_Task_Planning_of_Robotic_Agent

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, the main components of the method are:

1. Dataset Generation Pipeline:
- Character pool generation
- Input actions pool definition 
- Scenario creation using GPT-4 with retrieval from EmpatheticDialogues
- Empathy response generation using retrieved examples and GPT-4 selection

2. Training Methods:
- Instruction finetuning of LLaMA-3 8B
- RLHF training with reward model

The paper already includes ablations comparing:
- Different model architectures (GPT-4, LLaMA, etc.)
- Different input modalities (text vs video)
- Different training approaches (instruction tuning vs RLHF)

However, I notice two important missing ablations:

1. The impact of the retrieval component from EmpatheticDialogues during dataset generation. This is a critical part of ensuring diversity and quality of the generated scenarios and responses.

2. The effect of the character pool size and diversity on model performance. The paper uses 100 characters but doesn't analyze how this choice affects the final results.

These ablations would help understand the importance of key design choices in the method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### EmpatheticDialogues Retrieval Ablation
- **Ablated Part**: Retrieval from EmpatheticDialogues during dataset generation
- **Action**: REMOVE
- **Metrics**: BLEU-1, BLEU-4, ROUGE-L, CIDEr, SPICE, BERTScore, Overlap, TF-IDF, LCS

### Character Pool Size Ablation
- **Ablated Part**: Size and diversity of character pool
- **Action**: REPLACE
- **Replacement**: 
  - 25 characters
  - 50 characters
  - 200 characters
- **Metrics**: BLEU-1, BLEU-4, ROUGE-L, CIDEr, SPICE, BERTScore, Overlap, TF-IDF, LCS

</div>