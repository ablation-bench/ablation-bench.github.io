<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/blockskim

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, Block-Skim has several key components that warrant investigation through ablation studies:

1. The most critical component is the CNN-based block relevance predictor that uses diagonal attention weights. Testing this against using full attention weights or removing it entirely would validate their design choice.

2. The block size is an important hyperparameter that affects both accuracy and speedup. The paper uses 32 tokens per block but doesn't fully justify this choice.

3. The joint training approach with two objectives (QA loss and block-skim loss) is central to their method. Testing different loss weightings and removing components would help understand their contributions.

4. The layer-wise progressive skimming strategy, where blocks are skimmed at different layers, is a key design choice that could be compared to alternatives.

5. The diagonal attention region usage is a critical design choice that should be validated against using the full attention matrix.

I'll prioritize the most important ablations that would provide the most insight into the method's effectiveness.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Attention Region Ablation
- **Ablated Part**: diagonal attention region used for block prediction
- **Action**: REPLACE
- **Replacement**: 
  - full attention matrix
  - random attention region
  - vertical attention strip
- **Metrics**: F1 score, Exact Match, Speedup ratio

### Block Size Analysis
- **Ablated Part**: block size hyperparameter
- **Action**: REPLACE
- **Replacement**: 
  - 16
  - 64
  - 128
- **Metrics**: F1 score, Exact Match, Speedup ratio

### Loss Function Components
- **Ablated Part**: joint training with QA and block-skim losses
- **Action**: REMOVE
- **Metrics**: F1 score, Exact Match, Training convergence rate

### Progressive Skimming
- **Ablated Part**: layer-wise progressive block skimming
- **Action**: REPLACE
- **Replacement**: 
  - fixed skimming ratio
  - end-only skimming
- **Metrics**: F1 score, Exact Match, Speedup ratio

### CNN Architecture
- **Ablated Part**: CNN predictor architecture
- **Action**: REPLACE
- **Replacement**: 
  - MLP predictor
  - LSTM predictor
  - Transformer predictor
- **Metrics**: F1 score, Exact Match, Prediction accuracy

</div>