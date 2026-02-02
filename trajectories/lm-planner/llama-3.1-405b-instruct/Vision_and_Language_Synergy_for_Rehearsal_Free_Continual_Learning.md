<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Vision_and_Language_Synergy_for_Rehearsal_Free_Continual_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Vision and Language Synergy for Rehearsal-Free Continual Learning" proposes a novel approach for prompt-based continual learning. The method, called LEAPGen, incorporates four key concepts: language as input for prompt generation, task-wise generators, limiting matching descriptors search space via soft task-id prediction, and generated prompt as auxiliary data. The experimental analysis shows the superiority of LEAPGen to existing SOTAs in CIFAR100, ImageNet-R, and CUB datasets with significant margins.

To further evaluate the robustness of LEAPGen, we suggest two missing ablation studies:

1. **Ablation Study 1: Effect of Language Model Choice**
The current implementation of LEAPGen uses a specific language model (LLM) to generate descriptors. However, the choice of LLM may impact the performance of LEAPGen. This ablation study aims to investigate the effect of using different LLMs on the performance of LEAPGen.

* Ablated part: Language model used for descriptor generation
* Action: Replace the current LLM with alternative LLMs (e.g., BERT, RoBERTa, XLNet)
* Replacement: Use different LLMs to generate descriptors and evaluate the performance of LEAPGen
* Metrics: Report the average accuracy and average forgetting measure for each LLM

2. **Ablation Study 2: Effect of Task-Wise Generator Architecture**
The current implementation of LEAPGen uses a specific architecture for the task-wise generators. However, the choice of architecture may impact the performance of LEAPGen. This ablation study aims to investigate the effect of using different architectures for the task-wise generators.

* Ablated part: Task-wise generator architecture
* Action: Replace the current architecture with alternative architectures (e.g., MLP, LSTM, Transformer)
* Replacement: Use different architectures for the task-wise generators and evaluate the performance of LEAPGen
* Metrics: Report the average accuracy and average forgetting measure for each architecture
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Language model used for descriptor generation
- **Action**: REPLACE
- **Replacement**: 
  - BERT
  - RoBERTa
  - XLNet
- **Metrics**: average accuracy, average forgetting measure

### Ablation Study 2
- **Ablated Part**: Task-wise generator architecture
- **Action**: REPLACE
- **Replacement**: 
  - MLP
  - LSTM
  - Transformer
- **Metrics**: average accuracy, average forgetting measure

</div>