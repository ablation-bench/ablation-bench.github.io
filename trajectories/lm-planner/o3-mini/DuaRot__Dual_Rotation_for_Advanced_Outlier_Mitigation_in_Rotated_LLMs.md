<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/DuaRot__Dual_Rotation_for_Advanced_Outlier_Mitigation_in_Rotated_LLMs

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two missing ablation studies that focus on fundamental design choices in DuaRot but are not evaluated in the paper. First, given that the rotation matrices (both global and local) are initialized as the identity to inherit excellent initialization properties, it is important to study how sensitive the method is to this choice. An ablation comparing alternatives such as random orthogonal or scaled identity initialization could reveal whether the current initialization biases the optimization toward being dependent on the initialization and whether different initializations could lead to improved quantization error reduction and zero‐shot performance. Second, the method applies a sequential dual rotation (global followed by local) to refine features prior to merging. However, since rotations are non-commutative the ordering may affect how well outliers are mitigated. Evaluating alternative orders – such as reversing the sequence or even applying both rotations simultaneously (or in an interleaved manner) – would shed light on whether the current sequential scheme is optimal in terms of accuracy, inference speed, and downstream tasks.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Rotation Initialization Ablation
- **Ablated Part**: Initialization strategy for rotation matrices (global and local)
- **Action**: REPLACE
- **Replacement**: 
  - Identity Initialization
  - Random Orthogonal Initialization
  - Scaled Identity Initialization
- **Metrics**: WikiText-2 Perplexity, Zero-shot Accuracy

### Rotation Order Sensitivity Ablation
- **Ablated Part**: Sequential ordering of applying global and local rotations
- **Action**: REPLACE
- **Replacement**: 
  - Global-then-Local
  - Local-then-Global
  - Simultaneous Application
- **Metrics**: WikiText-2 Perplexity, Inference Speed, Zero-shot Accuracy

</div>