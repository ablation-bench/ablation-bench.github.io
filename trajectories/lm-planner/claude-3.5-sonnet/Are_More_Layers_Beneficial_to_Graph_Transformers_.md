<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Are_More_Layers_Beneficial_to_Graph_Transformers_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that while the authors conduct several ablation studies, there are two important aspects that lack thorough investigation:

1. The impact of substructure token dimension: The authors use substructure tokens as a key component but don't investigate how the dimension of these tokens affects performance. This is important since the token dimension could affect the model's ability to capture substructure information.

2. The effect of local attention ratio: While the authors introduce local attention on substructures, they don't explore how the balance between local and global attention affects performance. Understanding this trade-off could provide insights into optimizing the architecture.

The paper already includes ablations for:
- Local attention vs no local attention
- Substructure encoding vs no substructure encoding
- DeepNorm vs no DeepNorm
- Different types of substructures (geometric only vs neighbors only)
- Different neighbor sizes (5, 10, 15)

Therefore, my suggestions focus on the unexplored but important architectural choices that could significantly impact the model's performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Substructure Token Dimension Ablation
- **Ablated Part**: dimension of substructure token embeddings
- **Action**: REPLACE
- **Replacement**: 
  - 32
  - 64
  - 128
  - 256
- **Metrics**: MAE, Accuracy

### Local-Global Attention Ratio Ablation
- **Ablated Part**: ratio between local and global attention weights
- **Action**: REPLACE
- **Replacement**: 
  - 0.25
  - 0.5
  - 0.75
  - 1.0
- **Metrics**: MAE, Accuracy

</div>