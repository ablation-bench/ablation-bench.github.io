<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Nova__Generative_Language_Models_for_Assembly_Code_with_Hierarchical_Attention_and_Contrastive_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Nova: Generative Language Models for Assembly Code with Hierarchical Attention and Contrastive Learning" introduces Nova, a generative LLM specifically designed for assembly code. The key innovations include a hierarchical attention mechanism and contrastive learning objectives to address the challenges of low information density and diverse optimizations in assembly code. The paper presents ablation studies that demonstrate the effectiveness of these components, such as removing contrastive learning and hierarchical self-attention, and shows the impact on performance metrics like Pass@1 and Pass@10.

However, there are potential areas for further ablation studies that could provide additional insights into the model's performance. One such area is the hierarchical attention mechanism, which is applied to half of the attention heads. An ablation study could explore the impact of varying the proportion of attention heads using hierarchical attention. Another area is the contrastive learning objectives, specifically the functionality and optimization contrastive learning. An ablation study could investigate the impact of different weighting schemes for these objectives in the overall loss function.

These additional ablation studies would help to further understand the contribution of each component and design choice in Nova's architecture to its overall performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study on Hierarchical Attention Proportion
- **Ablated Part**: Proportion of attention heads using hierarchical attention
- **Action**: REPLACE
- **Replacement**: 
  - 0.25
  - 0.5
  - 0.75
  - 1.0
- **Metrics**: Pass@1, Pass@10, Recall@1

### Ablation Study on Contrastive Learning Weighting
- **Ablated Part**: Weighting of functionality and optimization contrastive learning objectives
- **Action**: REPLACE
- **Replacement**: 
  - 0.05
  - 0.1
  - 0.2
  - 0.3
- **Metrics**: Pass@1, Pass@10, Recall@1

</div>