<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/TIB__Detecting_Unknown_Objects_via_Two_Stream_Information_Bottleneck

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

From analyzing the paper, I notice that while the authors conducted several ablation studies, including:
1. Analysis of IB and RIB components separately (Table 4)
2. Analysis of branch numbers in MIB (Table 5) 
3. Analysis of hyperparameters β, λ, and τ
4. Analysis of different backbone networks (RegNetX vs ResNet)

However, there are two important ablation studies missing that could provide deeper insights:

1. The most critical missing ablation is an analysis of different discrepancy measures for Ldis in equation 8. The authors use absolute difference between predictions but don't justify this choice or compare it to alternatives like KL divergence or other distance metrics.

2. The second important missing ablation is an analysis of the gating mechanism design in equation 4. While they use a dot product attention-like mechanism, they don't compare it to simpler alternatives like concatenation or addition, which could reveal if this complexity is necessary.

These ablations would help understand if the specific design choices are optimal and necessary for the method's performance.

I'll focus on suggesting these two key missing ablations, ranked by importance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Discrepancy Loss Analysis
- **Ablated Part**: Loss function Ldis used for measuring prediction discrepancy between ID and OOD features
- **Action**: REPLACE
- **Replacement**: 
  - KL divergence
  - Jensen-Shannon divergence
  - Wasserstein distance
- **Metrics**: FPR95, AUROC, mAP

### Gating Mechanism Analysis
- **Ablated Part**: Gating mechanism used for aggregating information from multiple IB branches
- **Action**: REPLACE
- **Replacement**: 
  - Simple concatenation
  - Element-wise addition
  - Learned weighted sum
- **Metrics**: FPR95, AUROC, mAP

</div>