<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Nova__Generative_Language_Models_for_Assembly_Code_with_Hierarchical_Attention_and_Contrastive_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that the authors conducted ablation studies on several components of their method, specifically:

1. They ablated the contrastive learning (CL) and hierarchical attention (HA) components in Table 5, showing:
- Nova−CL−HA: Removing both CL and HA
- Nova−HA: Removing just HA
- Full Nova model

2. They also did additional ablation studies on the individual contrastive learning objectives in Table 11:
- Nova−FCL−HA: Removing functional CL and HA
- Nova−OCL−HA: Removing optimization CL and HA

However, I notice two important missing ablation studies that would help better understand the method's effectiveness:

1. The hierarchical attention mechanism is a key innovation but they don't fully ablate its different components (intra-instruction, preceding-instruction, and inter-instruction attention). Understanding the contribution of each attention type would be valuable.

2. While they test applying hierarchical attention to all vs half of the attention heads (Table 10), they don't explore different ratios or alternative ways of combining the attention types. This could help optimize the architecture.

I believe the first missing ablation is more important since the hierarchical attention is one of the two main technical contributions. Therefore, I'll focus my suggestions on ablating the attention components.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Hierarchical Attention Component Ablation
- **Ablated Part**: Individual components of the hierarchical attention mechanism (intra-instruction, preceding-instruction, and inter-instruction attention)
- **Action**: REMOVE
- **Metrics**: Pass@1, Pass@10, Recall@1

### Attention Head Ratio Study
- **Ablated Part**: Ratio of attention heads using hierarchical vs standard attention
- **Action**: REPLACE
- **Replacement**: 
  - 25%
  - 75%
  - 90%
- **Metrics**: Pass@1, Pass@10, Recall@1

</div>