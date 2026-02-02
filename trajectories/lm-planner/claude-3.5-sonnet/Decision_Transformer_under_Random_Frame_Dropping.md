<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Decision_Transformer_under_Random_Frame_Dropping

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper already includes several ablation studies, including:
1. Testing different placeholders for dropped frames (zeros, learnable masks, adding noise)
2. Testing different frame dropping processes (Bernoulli vs Markov)
3. Testing reconstruction of frames during training
4. Testing dropping actions along with observations
5. Testing different components of the drop-span embedding and finetuning

However, there are two important aspects that weren't thoroughly investigated:

1. The context length K is a critical hyperparameter for transformer-based methods, especially in scenarios with frame dropping where longer context might help bridge larger gaps. The paper uses fixed context lengths (K=20 for MuJoCo and K=30 for Atari) without investigating its impact.

2. The paper uses a fixed architecture (4 layers, 4 heads for MuJoCo; 6 layers, 8 heads for Atari) but doesn't investigate how model capacity affects robustness to frame dropping. This is particularly important since the model needs to learn both the task and handle missing information.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Context Length Ablation
- **Ablated Part**: transformer context length K
- **Action**: REPLACE
- **Replacement**: 
  - 10
  - 20
  - 40
  - 60
- **Metrics**: average returns, success rate

### Model Capacity Ablation
- **Ablated Part**: transformer architecture size
- **Action**: REPLACE
- **Replacement**: 
  - small (2 layers, 2 heads)
  - medium (4 layers, 4 heads)
  - large (8 layers, 8 heads)
- **Metrics**: average returns, success rate

</div>