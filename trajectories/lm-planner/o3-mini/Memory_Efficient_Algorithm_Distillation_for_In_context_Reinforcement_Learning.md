<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Memory_Efficient_Algorithm_Distillation_for_In_context_Reinforcement_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper already presents several ablation studies covering positional encodings, transformer model size, number of attention heads, and the trade-off between chunk length and recurrence capacity. However, two important design choices remain unexamined. First, the recurrence-based ED relies on a stop-gradient operation when incorporating past hidden states into current attention computations. This operator is critical to prevent unwanted gradient flow through long-term recurrence and to stabilize training; yet the paper does not investigate how sensitive the method is to this design. Removing or modifying the stop-gradient (e.g., allowing partial gradient flow) might affect both the in-context learning performance and training stability. Second, while the network architecture details mention using postnormalization (post-norm), the effect of the layer normalization position (pre-norm vs. post-norm) on both convergence and performance remains unexplored. Given that normalization arrangement can significantly alter gradient flow and training dynamics—especially in deep and recurrent Transformer settings—this ablation could provide insights into further optimizing ED for in-context reinforcement learning. These two ablations, ranked by importance, could yield useful directions to better understand and possibly improve the memory-efficient design.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Stop-Gradient Mechanism Ablation
- **Ablated Part**: Stop-gradient operator in the recurrence memory component of ERNIE-Docs
- **Action**: REPLACE
- **Replacement**: 
  - remove stop-gradient (allow full gradient flow)
  - apply partial stop-gradient (e.g., scale gradients by 0.5)
- **Metrics**: trajectory return, ICL performance, training stability

### LayerNorm Positioning Ablation
- **Ablated Part**: Positioning of the layer normalization (pre-norm vs. post-norm) in the ED architecture
- **Action**: REPLACE
- **Replacement**: 
  - pre-norm
  - post-norm
- **Metrics**: trajectory return, convergence rate, training stability

</div>