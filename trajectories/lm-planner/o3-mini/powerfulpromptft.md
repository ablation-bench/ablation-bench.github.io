<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/powerfulpromptft

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The proposed method—Prompt-based Continued Pre-training (PCP)—relies on several key components that distinguish it from conventional continued pre-training. First, the method introduces prompt templates (i.e. extra tokens and instructions) into the input during the unsupervised pre-training phase. An ablation where these prompt tokens are removed will directly measure the contribution of instruction tuning to downstream performance. Second, the additional continued pre-training step itself (using the constructed prompt-based corpus) is central to PCP; removing this step will show its overall benefit relative to direct prompt-based fine-tuning. Third, the corpus construction heavily depends on generating pseudo-labels for unlabelled data; varying or replacing this pseudo-label mechanism (for instance, using only golden labels or fixed tokens) helps isolate its impact. Fourth, the exact design of the prompt template (e.g., minimal versus elaborated instructions) may affect performance, so testing different designs will provide insight into optimal settings. Finally, the use of the verbalizer function M(·) embeds label-specific information in the prompts. Replacing these tokens with constant or random signals will reveal its effect. The following five ablation studies, ranked by importance, thus address the major components of PCP and report commonly used metrics such as accuracy and F1 on the 21 benchmarks considered.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Remove Prompt-Template Guidance
- **Ablated Part**: The addition of prompt template tokens (instruction signals) to the input during continued pre-training
- **Action**: REMOVE
- **Metrics**: accuracy, F1 score, benchmark average improvement

### Remove Additional Continued Pre-training Step
- **Ablated Part**: The extra unsupervised pre-training using the constructed prompt-based corpus
- **Action**: REMOVE
- **Metrics**: accuracy, F1 score, absolute performance change

### Pseudo-labeling Strategy Ablation
- **Ablated Part**: The pseudo-label generation on unlabelled data during corpus construction
- **Action**: REPLACE
- **Replacement**: 
  - use only golden labels
  - use fixed dummy label tokens
- **Metrics**: accuracy, F1 score, calibration error

### Prompt Template Design Ablation
- **Ablated Part**: The design of prompt templates used in forming the PCP corpus
- **Action**: REPLACE
- **Replacement**: 
  - minimal prompt template
  - elaborated prompt template
- **Metrics**: accuracy, F1 score

### Verbalizer Function Ablation
- **Ablated Part**: The inclusion of label-specific tokens via the verbalizer function M(y) in the prompt
- **Action**: REPLACE
- **Replacement**: 
  - constant token
  - random token
- **Metrics**: accuracy, F1 score

</div>