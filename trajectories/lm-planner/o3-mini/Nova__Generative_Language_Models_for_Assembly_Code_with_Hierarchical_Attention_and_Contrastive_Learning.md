<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Nova__Generative_Language_Models_for_Assembly_Code_with_Hierarchical_Attention_and_Contrastive_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

In Nova the hierarchical attention module is central to the design and has three components (intra‐instruction, preceding‐instruction, and inter‐instruction attention). Although the paper shows an ablation where the entire hierarchical attention is removed (Nova^-HA) and further an experiment replacing it with LongCoder’s window attention, it does not isolate the contribution of individual attention components. Thus, one important missing ablation is to evaluate the effect of removing one or more of the hierarchical attention submodules (for example, by removing only the preceding-instruction attention, only the inter-instruction attention, or both) on downstream performance metrics (Pass@1, Pass@10 on decompilation and Recall@1 on similarity detection).

Another key novelty of Nova is the addition of contrastive learning objectives that are integrated into the total loss alongside language modeling with a weighting factor λ set to 0.1. Though the paper does compare cases when contrastive learning is entirely removed (Nova^-CL-HA) versus when it is present, it does not investigate how sensitive the performance is to different settings of λ. A systematic ablation that varies this hyperparameter (including setting it to 0 to mimic the removal of contrastive learning) would help better understand the optimization trade-offs and gain deeper insights into the interactions between the language modeling and contrastive objectives.

The following JSONL proposals capture these two most important missing ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Hierarchical Attention Component Ablation
- **Ablated Part**: Components of Nova's hierarchical attention mechanism; specifically the preceding-instruction and inter-instruction attention modules
- **Action**: REPLACE
- **Replacement**: 
  - Remove preceding-instruction attention
  - Remove inter-instruction attention
  - Remove both preceding- and inter-instruction attention
- **Metrics**: Pass@1, Pass@10, Recall@1

### Contrastive Learning Weight Ablation
- **Ablated Part**: Weight (λ) assigned to the contrastive learning objectives in the joint loss function
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.05
  - 0.1
  - 0.2
  - 0.5
- **Metrics**: Pass@1, Pass@10, Recall@1

</div>