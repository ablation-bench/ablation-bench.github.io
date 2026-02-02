<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/blockskim

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Below is the plan for five targeted ablation studies that dissect the key building blocks of Block‐Skim. First, we propose to remove the block-skim module entirely to gauge its impact on both QA accuracy and inference speed relative to the vanilla Transformer. Second, we investigate the input features fed to the CNN block-relevance predictor: by replacing the full attention heatmap input with only the diagonal region, we can validate the hypothesis that the diagonal carries most of the useful information and also lower the computational overhead. Third, we examine the training paradigm by comparing joint multi-objective training (where the QA loss and the block-skim loss are optimized together) versus a decoupled or sequential training of the block predictor; this study will reveal how strongly the extra supervision helps the attention mechanism. Fourth, we plan to vary the loss balancing hyperparameters (harmony coefficient α and balance factor β) in the total loss formulation so as to understand their effect on convergence, QA performance, and the trade-off between positive/negative block weighting. Finally, we propose replacing the CNN architecture for predicting block relevance with simpler alternatives (e.g., an MLP or a linear classifier) to study the trade-offs in accuracy and speed. These prioritized ablation studies will help isolate the contributions of the key components and guide further improvements.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Block-Skim Module Removal
- **Ablated Part**: Entire block-level relevance prediction (Block-Skim plug-in) that skims irrelevant blocks during inference
- **Action**: REMOVE
- **Metrics**: QA accuracy, F1 score, Inference speedup

### Attention Input Variant
- **Ablated Part**: Input representation to the block relevance predictor from the transformer attention; specifically, full attention heatmap versus diagonal region only
- **Action**: REPLACE
- **Replacement**: 
  - full attention heatmap
  - diagonal region only
- **Metrics**: Block predictor accuracy, QA accuracy, Inference latency

### Training Paradigm Comparison
- **Ablated Part**: The joint multi-objective loss that combines the QA objective with the block-level (Block-Skim) objective
- **Action**: REPLACE
- **Replacement**: 
  - joint multi-objective training
  - decoupled/sequential training of block predictor
- **Metrics**: QA accuracy, Block prediction accuracy, Training stability/convergence

### Loss Balance Hyperparameter Tuning
- **Ablated Part**: The weighting factors (harmony coefficient α and balance factor β) in the combined loss function
- **Action**: REPLACE
- **Replacement**: 
  - α = 0.1, 0.5, 1.0
  - β = 0.5, 1.0, 2.0
- **Metrics**: QA accuracy, Block predictor accuracy, Convergence rate

### Predictor Architecture Simplification
- **Ablated Part**: The CNN architecture used for processing attention heatmap features for block relevance prediction
- **Action**: REPLACE
- **Replacement**: 
  - CNN
  - MLP
  - Linear layer
- **Metrics**: Block prediction accuracy, Overall QA performance, Inference latency

</div>