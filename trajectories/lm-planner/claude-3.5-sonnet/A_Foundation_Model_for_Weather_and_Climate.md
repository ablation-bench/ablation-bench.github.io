<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/A_Foundation_Model_for_Weather_and_Climate

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents Prithvi WxC, a foundation model for weather and climate applications. From reviewing the ablation studies already present in the paper:

1. They ablated the use of climatology in the pretraining objective (Section B.2.1)
2. They ablated the masking strategy (Section B.2.1) 
3. They ablated the handling of lead time signal (Section B.2.2)
4. They ablated the use of context tokens (Section B.2.2)
5. They performed scaling experiments comparing 280M vs 2.3B parameters (Section B.2.2)

Looking at the core components of the method, I identify two important missing ablation studies:

1. The architecture uses a combination of local and global attention patterns, alternating between them in both encoder and decoder. However, there's no ablation studying the importance of this dual attention mechanism compared to using just one type.

2. The model uses a mixed objective combining masked reconstruction with forecasting, but there's no ablation studying different ratios between these two objectives in the loss function.

These would be valuable ablations since they test core design choices of the method that significantly impact its performance and capabilities.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Attention Pattern Ablation
- **Ablated Part**: dual attention mechanism (local+global)
- **Action**: REPLACE
- **Replacement**: 
  - local attention only
  - global attention only
- **Metrics**: reconstruction RMSE, forecasting RMSE, memory usage, computational time

### Loss Objective Ratio Ablation
- **Ablated Part**: ratio between masked reconstruction and forecasting objectives
- **Action**: REPLACE
- **Replacement**: 
  - 100% masking / 0% forecasting
  - 75% masking / 25% forecasting
  - 25% masking / 75% forecasting
  - 0% masking / 100% forecasting
- **Metrics**: reconstruction loss, forecasting loss, combined loss

</div>