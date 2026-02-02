<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/DuaRot__Dual_Rotation_for_Advanced_Outlier_Mitigation_in_Rotated_LLMs

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that while there are comprehensive ablations on the dual rotation components and hardware-aware matrix configuration, there are some important aspects that weren't fully explored:

1. The first missing ablation relates to the initialization strategy of the rotation matrices. While the paper mentions initializing R^i_L as identity matrix to "inherit the excellent initialization properties of R1", there's no ablation studying different initialization strategies and their impact. This is important since initialization can significantly affect optimization and final performance.

2. The second missing ablation relates to the number of groups (n) in the local rotation matrix R^L. The paper sets this as a fixed hyperparameter but doesn't explore how different group sizes affect the trade-off between computational efficiency and outlier mitigation effectiveness. This is particularly important since the group size directly impacts both training and inference.

The metrics used in the paper are primarily perplexity (PPL) on WikiText-2 and accuracy on zero-shot tasks like PIQA, WinoGrande, HellaSwag, etc. These should be maintained for consistency in the ablation studies.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Rotation Matrix Initialization Ablation
- **Ablated Part**: initialization strategy of rotation matrices
- **Action**: REPLACE
- **Replacement**: 
  - random orthogonal initialization
  - Hadamard initialization
  - identity initialization
- **Metrics**: WikiText-2 perplexity, zero-shot task accuracy

### Local Rotation Groups Ablation
- **Ablated Part**: number of groups in local rotation matrix R^L
- **Action**: REPLACE
- **Replacement**: 
  - n=2
  - n=4
  - n=8
  - n=16
- **Metrics**: WikiText-2 perplexity, zero-shot task accuracy

</div>