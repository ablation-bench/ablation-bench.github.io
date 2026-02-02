<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/curriculum_learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents a curriculum learning approach with several key components that warrant investigation through ablation studies:

1. The most critical component is the difficulty scoring functions (QAP, Variability, Energy) used to rank samples. Testing each scoring method independently is important.

2. The paper uses both fixed and adaptive curriculum learning approaches. The adaptive approach includes a key innovation of flipping to difficult-to-easy curriculum in later stages.

3. The pacing function with its parameters (starting percentage, increase factor, step length) is central to controlling how samples are introduced.

4. The paper uses both full model fine-tuning and parameter-efficient prompt-tuning settings.

Based on these components, I'll suggest the most important ablation studies to validate the method's key contributions.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Scoring Function Ablation
- **Ablated Part**: Different difficulty scoring functions used for ranking samples
- **Action**: REPLACE
- **Replacement**: 
  - QAP only
  - Variability only
  - Energy only
  - Random scoring
- **Metrics**: Accuracy, F1 score

### Curriculum Adaptation
- **Ablated Part**: Adaptive curriculum with difficulty-to-easy flip
- **Action**: REPLACE
- **Replacement**: 
  - Fixed curriculum only
  - Adaptive without flip
  - Random order
- **Metrics**: Accuracy, F1 score, Out-of-domain performance

### Pacing Function
- **Ablated Part**: Pacing function parameters
- **Action**: REPLACE
- **Replacement**: 
  - Linear pacing
  - Step function
  - No pacing (all data at once)
- **Metrics**: Accuracy, F1 score, Training convergence rate

### Training Regime
- **Ablated Part**: Combined full fine-tuning and prompt-tuning
- **Action**: REPLACE
- **Replacement**: 
  - Full fine-tuning only
  - Prompt-tuning only
- **Metrics**: Accuracy, F1 score, Parameter efficiency

</div>