<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Video_STaR__Self_Training_Enables_Video_Instruction_Tuning_with_Any_Supervision

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that the authors have conducted some ablation studies (shown in Tables 6 and 7) focusing on:
1. Removing Answer Generation
2. Removing Label Rationalization 

However, there are some critical components of the Video-STaR method that weren't ablated:

1. The Label Verification component is crucial as it filters the generated answers based on whether they contain the correct labels. The paper uses a mixture of named entity recognition and Regex for verification, but doesn't investigate how different verification methods impact performance.

2. The cycling mechanism (number of cycles) is a key part of the method, but there's no systematic study of how performance changes with different numbers of cycles. While they mention using 3 cycles, it's not clear if this is optimal.

Based on this analysis, I'll suggest the two most important missing ablation studies that would help better understand the method's performance:

1. Label Verification Methods: This is critical as it directly impacts which answers are selected for training and thus the quality of the instruction tuning dataset.

2. Number of Cycles: This is fundamental to understanding the self-training dynamics and finding the optimal training regime.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Label Verification Methods Ablation
- **Ablated Part**: Parser-Verifier component that uses named entity recognition and Regex for label verification
- **Action**: REPLACE
- **Replacement**: 
  - Only Regex matching
  - Only NER
  - BERT similarity matching
  - Exact string matching
- **Metrics**: Accuracy, Score, Generation Yield

### Number of Cycles Ablation
- **Ablated Part**: Number of self-training cycles
- **Action**: REPLACE
- **Replacement**: 
  - 1 cycle
  - 2 cycles
  - 4 cycles
  - 5 cycles
- **Metrics**: Accuracy, Score, Generation Yield, Training Time

</div>