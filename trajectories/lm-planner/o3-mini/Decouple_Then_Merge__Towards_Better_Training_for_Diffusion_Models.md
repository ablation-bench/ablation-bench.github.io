<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Decouple_Then_Merge__Towards_Better_Training_for_Diffusion_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper already presents ablation studies on the basic components of the decoupled training framework (e.g., the effects of probabilistic sampling, consistency loss, and channel‐wise projection, as well as sensitivity to N and p). However, two important aspects remain unexplored. First, the merging scheme itself relies on merging weights that are determined by grid search to combine task vectors from different timestep finetunings. There is no investigation into whether different weight strategies (for example, simple uniform averaging, a weighting scheme based on SNR statistics, or even learnable weight parameters) would lead to different performance outcomes. Such an ablation is critical because the merge step is central to the method’s efficiency and effectiveness. Second, while the paper uses a channel‐wise projection to capture timestep-specific feature differences, it would be informative to see whether alternative projection designs (such as a spatial-only projection or a combination of channel and spatial projections) might benefit or hurt performance. Evaluating different projection module designs can help to pinpoint the crucial aspects of feature adaptation in the finetuning phase. Both ablations would be evaluated using the key metrics from the paper – FID for unconditional generation and CLIP score for text-to-image generation.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Merge Weight Strategy Ablation
- **Ablated Part**: Merging scheme: the choice of merging weights (w_i) used to combine task vectors across timestep ranges
- **Action**: REPLACE
- **Replacement**: 
  - uniform averaging
  - SNR-based weighting
  - learnable weight parameters
- **Metrics**: FID, CLIP Score

### Projection Module Design Ablation
- **Ablated Part**: Projection module design for capturing timestep-specific feature differences during finetuning
- **Action**: REPLACE
- **Replacement**: 
  - Channel-wise Projection (baseline)
  - Spatial Projection
  - Combined Channel-Spatial Projection
- **Metrics**: FID, CLIP Score

</div>