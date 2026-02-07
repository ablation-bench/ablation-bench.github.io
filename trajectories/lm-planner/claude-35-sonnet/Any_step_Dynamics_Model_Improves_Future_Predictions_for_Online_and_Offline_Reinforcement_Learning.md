<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Any_step_Dynamics_Model_Improves_Future_Predictions_for_Online_and_Offline_Reinforcement_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents ADM (Any-step Dynamics Model) which allows variable-length plans as inputs for predicting future states. The authors already conducted several ablation studies including:

1. Comparing ADM against ensemble dynamics model and bootstrapping RNN in terms of compounding error
2. Testing different values of maximum backtracking length m (1,5,10,15,20)
3. Comparing different uncertainty quantifier choices (max aleatoric, max pairwise difference, prediction std)
4. Testing different prediction choices (priority sampling, max backtracking, average prediction)

However, I notice two important missing ablation studies:

1. The RNN architecture choice - The authors mention they use GRU cells but don't investigate the impact of different RNN architectures. This is important since the RNN is a core component for handling variable-length sequences.

2. The state duplication strategy - The authors duplicate the input state to match the action sequence length but don't explore alternative approaches. This design choice could significantly impact model performance.

These ablations would help better understand the method's key architectural components.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### RNN Architecture Ablation
- **Ablated Part**: GRU cell in the RNN architecture
- **Action**: REPLACE
- **Replacement**: 
  - LSTM
  - Vanilla RNN
  - Transformer
- **Metrics**: model mean squared error, compounding error, normalized score

### State Input Strategy Ablation
- **Ablated Part**: state duplication strategy for matching action sequence length
- **Action**: REPLACE
- **Replacement**: 
  - zero padding
  - learnable padding
  - state embedding
- **Metrics**: model mean squared error, compounding error, normalized score

</div>