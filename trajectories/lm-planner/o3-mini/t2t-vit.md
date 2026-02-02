<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/t2t-vit

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The following ablation studies focus on isolating the key contributions of the paper. First, we assess the impact of the progressive tokenization mechanism by completely removing the Tokens-to-Token (T2T) module—which is designed to aggregate local structure information via a re-structurization and soft split process—so that we can directly compare with the standard fixed patch splitting used in vanilla ViT. Second, we study the effect of the soft split (i.e. overlapping patch splits) by replacing it with a hard, non-overlapping split or by varying the overlap ratios to determine its influence on capturing local structure. Third, we evaluate the efficiency gain from the deep-narrow transformer backbone used in T2T-ViT by replacing it with a shallow-wide structure (similar to that of the vanilla ViT) to gauge changes in model capacity, redundancy, and feature richness. Finally, we examine the specific implementation choice inside the T2T module by replacing the efficient Performer layer with a standard Transformer layer (or vice versa) and checking its effect on top-1 accuracy, memory usage, and computation (MACs). These four studies are ranked as the most impactful in attributing performance improvements to the major architectural components.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove T2T Module
- **Ablated Part**: Progressive tokenization module that aggregates local structure via Tokens-to-Token transformations
- **Action**: REMOVE
- **Metrics**: top-1 accuracy, MACs, Params

### Ablation: Hard Split vs Soft Split
- **Ablated Part**: Local tokenization strategy in the T2T module (soft split with overlapping patches)
- **Action**: REPLACE
- **Replacement**: 
  - non-overlapping patch split
  - varying overlap ratios
- **Metrics**: top-1 accuracy, MACs

### Ablation: Backbone Architecture Design
- **Ablated Part**: Transformer backbone architecture (deep-narrow design vs. shallow-wide design)
- **Action**: REPLACE
- **Replacement**: 
  - shallow-wide transformer backbone as in vanilla ViT
  - alternative depth/channel configurations
- **Metrics**: top-1 accuracy, MACs, Params

### Ablation: T2T Transformer Layer Variant
- **Ablated Part**: Type of transformer layer used within the T2T module
- **Action**: REPLACE
- **Replacement**: 
  - Standard Transformer layer
  - Performer layer
- **Metrics**: top-1 accuracy, memory usage, MACs

</div>