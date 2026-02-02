<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/SEAL__Safety_enhanced_Aligned_LLM_Fine_tuning_via_Bilevel_Data_Selection

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the SEAL paper, I'll suggest missing ablation studies that could help better understand the method's key components. Let me first summarize the existing ablations:

1. The paper tests different data selection percentages (20%-80%) in Section 4.3
2. They test transferability between different models in Section 4.4
3. They test performance with different ratios of unsafe data in Appendix B.4

Looking at the core components of SEAL, I notice two important aspects that lack ablation studies:

1. The penalty strength parameter γ: This is a crucial hyperparameter that controls the trade-off between safety loss and fine-tuning loss in the bilevel optimization. While the paper mentions γ increases by a fixed amount each epoch, there's no ablation studying its impact.

2. The data selector function σ(ω): The paper uses softmax but doesn't explore alternatives. Different selector functions could impact the method's effectiveness.

I'll suggest these as missing ablation studies, focusing on the metrics used in the paper (win rates on ANTHROPIC HH test, SLIMORCA test, and HEX-PHI).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Penalty Strength Ablation
- **Ablated Part**: penalty strength parameter γ in bilevel optimization
- **Action**: REPLACE
- **Replacement**: 
  - 0.01
  - 0.05
  - 0.1
  - 0.2
- **Metrics**: ANTHROPIC HH test win rate, SLIMORCA test win rate, HEX-PHI win rate

### Selector Function Ablation
- **Ablated Part**: data selector function σ(ω)
- **Action**: REPLACE
- **Replacement**: 
  - sigmoid
  - tanh
  - ReLU
- **Metrics**: ANTHROPIC HH test win rate, SLIMORCA test win rate, HEX-PHI win rate

</div>