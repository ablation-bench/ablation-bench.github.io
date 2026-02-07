<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Quantifying_and_Enhancing_Multi_modal_Robustness_with_Modality_Preference

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

First, let me identify the key ablation studies already present in the paper:
1. The paper includes ablation studies on their two-step training procedure (CRMT-step-1 and CRMT-step-2) as shown in Figure 5.
2. They also test their method with different architectures (extending to transformers) as shown in Table 3.

After analyzing the paper, I identify two critical missing ablation studies:

1. The orthogonality constraint in their framework is a major design choice that affects how the uni-modal classifiers work. While they mention it helps decouple the learning of uni-modal representations and integration, they don't ablate different ways to achieve this decoupling or test how strict this orthogonality needs to be.

2. The paper proposes using modality-specific weights a(m) to focus on more reliable modalities, but doesn't ablate different ways of computing these weights. This is crucial since the weights directly affect how the model balances information from different modalities.

These ablations would help better understand the method's key components and potentially lead to improvements in the approach.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Orthogonality Constraint Ablation
- **Ablated Part**: Orthogonality constraint between uni-modal classifier rows
- **Action**: REPLACE
- **Replacement**: 
  - Soft orthogonality with penalty term
  - Partial orthogonality between subset of rows
  - No orthogonality
- **Metrics**: Clean accuracy, FGM accuracy, ℓ2-PGD accuracy

### Modality Weight Computation
- **Ablated Part**: Modality-specific weight computation method
- **Action**: REPLACE
- **Replacement**: 
  - Learned weights through backprop
  - Fixed equal weights
  - Confidence-based dynamic weights
- **Metrics**: Clean accuracy, Uni-modal attack accuracy (#v and #a), Multi-modal attack accuracy

</div>