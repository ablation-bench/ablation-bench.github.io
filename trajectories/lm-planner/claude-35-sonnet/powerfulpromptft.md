<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/powerfulpromptft

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, PCP consists of two main steps:
1. Constructing continued pre-training corpus by combining task-related texts with prompt templates
2. Performing continued pre-training using MLM objective and then prompt-based fine-tuning

The key novel aspects that deserve ablation studies are:

1. The use of prompt templates during continued pre-training - this is the main innovation and should be tested by removing it.

2. The pseudo-labeling process - the method uses a trained model to generate pseudo-labels for unlabeled examples, which could be compared to using random labels or no labels.

3. The MLM objective - while the paper uses MLM, other pre-training objectives could be tested.

4. The two-step process - the method first trains a model for pseudo-labeling and then trains another model with PCP, which could be compared to a single-step approach.

5. The combination of task-related texts and prompts - testing different mixing strategies could be valuable.

I'll prioritize the most important ablations that would help understand the key contributions.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Remove Prompt Templates
- **Ablated Part**: prompt templates during continued pre-training
- **Action**: REMOVE
- **Metrics**: accuracy, F1-score

### Pseudo-label Quality
- **Ablated Part**: pseudo-labeling process
- **Action**: REPLACE
- **Replacement**: 
  - random labels
  - no labels
  - gold labels only
- **Metrics**: accuracy, F1-score

### Pre-training Objective
- **Ablated Part**: MLM objective
- **Action**: REPLACE
- **Replacement**: 
  - causal language modeling
  - prefix language modeling
- **Metrics**: accuracy, F1-score

### Training Process
- **Ablated Part**: two-step training process
- **Action**: REPLACE
- **Replacement**: 
  - single-step training with direct pseudo-labeling
- **Metrics**: accuracy, F1-score, training time

</div>