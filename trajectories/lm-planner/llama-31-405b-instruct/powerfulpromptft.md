<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-31-405b-instruct/powerfulpromptft

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Don't Stop Pretraining? Make Prompt-based Fine-tuning Powerful Learner" presents a novel approach to fine-tuning language models, called Prompt-based Continued Pre-training (PCP). The authors argue that conventional continued pre-training may not always be beneficial for fine-tuning, especially for sentence-pair tasks or when using prompt-based fine-tuning. They propose PCP as a solution, which combines the idea of instruction tuning with conventional continued pre-training. The approach involves constructing a continued pre-training corpus by generating pseudo-labels for unlabelled examples and then fine-tuning the model using prompt-based fine-tuning.

To investigate the effectiveness of PCP, I suggest the following ablation studies:

1. **Removing the pseudo-label generation step**: This ablation study will help us understand the importance of generating pseudo-labels for unlabelled examples in the PCP approach. By removing this step, we can see how much the pseudo-labels contribute to the overall performance of the model.

2. **Replacing the MLM objective with a different objective**: The PCP approach uses the masked language modeling (MLM) objective for continued pre-training. This ablation study will help us understand the impact of using a different objective, such as next sentence prediction (NSP) or sentence classification, on the performance of the model.

3. **Using a different prompt template**: The PCP approach uses a specific prompt template for fine-tuning. This ablation study will help us understand the impact of using a different prompt template on the performance of the model.

4. **Removing the continued pre-training step**: This ablation study will help us understand the importance of continued pre-training in the PCP approach. By removing this step, we can see how much the continued pre-training contributes to the overall performance of the model.

5. **Using a different model architecture**: The PCP approach uses a specific model architecture, such as BERT or RoBERTa. This ablation study will help us understand the impact of using a different model architecture on the performance of the model.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: pseudo-label generation step
- **Action**: REMOVE
- **Metrics**: accuracy, F1 score

### Ablation 2
- **Ablated Part**: MLM objective
- **Action**: REPLACE
- **Replacement**: 
  - NSP
  - sentence classification
- **Metrics**: accuracy, F1 score

### Ablation 3
- **Ablated Part**: prompt template
- **Action**: REPLACE
- **Replacement**: 
  - template 1
  - template 2
  - template 3
- **Metrics**: accuracy, F1 score

### Ablation 4
- **Ablated Part**: continued pre-training step
- **Action**: REMOVE
- **Metrics**: accuracy, F1 score

### Ablation 5
- **Ablated Part**: model architecture
- **Action**: REPLACE
- **Replacement**: 
  - BERT
  - RoBERTa
  - ALBERT
- **Metrics**: accuracy, F1 score

</div>