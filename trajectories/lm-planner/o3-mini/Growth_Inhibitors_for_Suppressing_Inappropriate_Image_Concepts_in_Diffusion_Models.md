<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Growth_Inhibitors_for_Suppressing_Inappropriate_Image_Concepts_in_Diffusion_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two missing ablation studies that examine key design choices in the GIE method. First, while the paper employs an adapter—a two-hidden-layer MLP—to infer an optimal suppression scale from the intermediate cross‐attention values, the paper does not explore whether this specific architecture is critical for balancing the erasure effect and semantic preservation. An ablation study replacing the adapter with simpler (e.g. linear regression or a single hidden layer) or more complex (e.g. deeper MLP with three hidden layers) alternatives would determine the sensitivity of the overall performance to the adapter’s architecture.
Second, the method extracts the target concept features from the cross-attention map by discarding the boundary tokens ([SOT] and [EOT]). However, the paper does not investigate how this extraction window affects the erasure performance. An ablation study that varies the extraction window – for example, including one or both of the boundary tokens or selecting different token subsets – would provide insight into how precisely the target feature representation contributes to effective growth inhibitor synthesis. Both studies can be evaluated using metrics already reported in the paper such as NSFW Removal Rate (NRR), FID, CLIP score, and, when applicable, Object Removal Rate (ORR).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Adapter Architecture Ablation
- **Ablated Part**: The adapter network used to infer the optimal suppression scale from the cross-attention intermediate values.
- **Action**: REPLACE
- **Replacement**: 
  - linear regression
  - single hidden layer MLP
  - deeper MLP with three hidden layers
- **Metrics**: NSFW Removal Rate (NRR), FID, CLIP score

### Target Feature Extraction Window Ablation
- **Ablated Part**: The extraction window for target concept features from the attention map (i.e., excluding [SOT] and [EOT] tokens).
- **Action**: REPLACE
- **Replacement**: 
  - include [SOT] token
  - include [EOT] token
  - include both [SOT] and [EOT] tokens
  - use only central token
- **Metrics**: NSFW Removal Rate (NRR), FID, CLIP score, Object Removal Rate (ORR)

</div>