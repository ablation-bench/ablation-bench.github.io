<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Learn_while_Unlearn__An_Iterative_Unlearning_Framework_for_Generative_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents ICU (Iterative Contrastive Unlearning), which consists of three main components:
1. Knowledge Unlearning Induction (KUI) module
2. Contrastive Learning Enhancement (CLE) module 
3. Iterative Unlearning Refinement (IUR) module

The paper already includes some ablation studies:
- Ablation of the learning enhancement losses (pair learning loss and KL-divergence loss)
- Parameter sensitivity analysis for α and β hyperparameters

However, there are some important missing ablations that could provide deeper insights:

1. The most critical missing ablation is on the KNN sampling strategy in the CLE module. The paper uses K=1 nearest neighbor but doesn't justify this choice or explore alternatives. Testing different K values or alternative sampling strategies would help understand the impact of this design choice.

2. Another important missing ablation is on the IUR module's thresholds (a=0.3 and b=0.01). These thresholds determine when to stop unlearning specific data pieces but their impact is not analyzed. Testing different threshold values would help understand their effect on the unlearning process.

I'll focus on these two ablations as they target core components of the method and their impact is not explored in the current paper.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### KNN Sampling Strategy Ablation
- **Ablated Part**: KNN sampling in Contrastive Learning Enhancement module
- **Action**: REPLACE
- **Replacement**: 
  - K=3
  - K=5
  - K=10
  - Random sampling
- **Metrics**: EL10, MA, BERT, Entropy, Cls Avg., Dia Avg., Pile PPL, Wikitext PPL, GPT

### IUR Thresholds Ablation
- **Ablated Part**: Thresholds in Iterative Unlearning Refinement module
- **Action**: REPLACE
- **Replacement**: 
  - a=0.2,b=0.005
  - a=0.4,b=0.015
  - a=0.5,b=0.02
- **Metrics**: EL10, MA, BERT, Entropy, Cls Avg., Dia Avg., Pile PPL, Wikitext PPL, GPT

</div>