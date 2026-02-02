<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Shadow_Alignment__The_Ease_of_Subverting_Safely_Aligned_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Let me analyze the paper and suggest important missing ablation studies:

1. The paper performs shadow alignment attacks using 100 malicious examples on various models. A key finding is that this small amount of data is sufficient to break safety measures. However, they don't ablate the training data composition - specifically, they don't investigate how the ratio of different types of harmful content in the training data affects the attack success. This is important since they use 13 different forbidden scenarios.

2. The paper shows that single-turn English training generalizes well to multi-turn dialogues and other languages. However, they don't ablate the model architecture components to understand what enables this generalization capability. Specifically, they don't investigate which model components (attention layers, feed-forward networks, etc.) are most responsible for the transfer of harmful behaviors.

Looking at the existing ablations in the paper:
- They ablate the number of training examples (50, 100, 500, 2000)
- They ablate the number of forbidden scenarios used in training
- They ablate hyperparameters like learning rate, batch size and number of epochs

Therefore, I suggest the following two most important missing ablations:

1. Ablating the composition of training data by varying the ratio of different harmful content types, to understand if certain combinations make the attack more effective.

2. Ablating model architecture components through selective freezing/unfreezing during fine-tuning, to identify which parts enable cross-lingual and multi-turn transfer of harmful behaviors.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Training Data Composition Ablation
- **Ablated Part**: Ratio of different harmful content types in the 100 training examples
- **Action**: REPLACE
- **Replacement**: 
  - Equal ratio across all 13 scenarios
  - Focus on 3-4 key scenarios with 80% examples
  - Random sampling without controlling ratios
- **Metrics**: Violation rate, Harmfulness score, Human preference score

### Architecture Component Ablation
- **Ablated Part**: Model components enabled during fine-tuning
- **Action**: REPLACE
- **Replacement**: 
  - Only tune attention layers
  - Only tune feed-forward layers
  - Only tune final layers
  - Tune all layers
- **Metrics**: Cross-lingual violation rate, Multi-turn dialogue violation rate, General benchmark performance

</div>