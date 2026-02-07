<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Local_Prompt__Extensible_Local_Prompts_for_Few_Shot_Out_of_Distribution_Detection

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on my analysis of the paper, there are two important ablation studies missing that could provide deeper insights:

1. The impact of the number of local prompts per class:
- The paper uses one local prompt per known category (1000 for ImageNet-1k) but doesn't ablate this design choice
- This is a critical hyperparameter that could affect both performance and computational efficiency
- Testing different numbers of local prompts per class would reveal if more/fewer prompts could achieve better results

2. The effect of different regional regularization strategies:
- The paper proposes contrastive and diversity regularization but doesn't fully explore alternative regularization approaches
- The interaction between these two regularization terms is not thoroughly analyzed
- Testing different combinations and alternative regularization strategies would provide insights into the optimal regularization setup

The paper already includes ablations for:
- Loss components (Table 6)
- Negative augmentation strategies (Table 7) 
- Number of local negative prompts (Table 8)
- Regional number k (Figure 7)
- Training time (Table 11)
- Number of negative augmentations (Table 12)

Therefore, I'll focus on the two most important missing ablations that could provide valuable insights into core design choices of the method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Local Prompts Per Class Ablation
- **Ablated Part**: Number of local prompts per class
- **Action**: REPLACE
- **Replacement**: 
  - 0.5x prompts per class
  - 2x prompts per class
  - 4x prompts per class
- **Metrics**: FPR95, AUROC, ID accuracy

### Regional Regularization Strategy Ablation
- **Ablated Part**: Regional regularization approach
- **Action**: REPLACE
- **Replacement**: 
  - L2 regularization
  - KL divergence regularization
  - Cosine similarity regularization
- **Metrics**: FPR95, AUROC, ID accuracy

</div>