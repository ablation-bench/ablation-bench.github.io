<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Zero_Shot_Video_Sampling_from_Image

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The first missing ablation study we propose targets the Temporal Momentum Attention (TMA) module. Although the paper introduces TMA as a novel means to balance between self-attention and cross-frame attention, it does not report an ablation that isolates its impact. Replacing TMA with pure self-attention (by setting µ = 0) or pure cross-frame attention (by setting µ = 1), as well as testing several intermediate µ values (e.g., 0.6, 0.8, 0.98), would help quantify how the momentum mechanism contributes to both temporal consistency and overall video quality. The metrics for this study should include the CLIP score (to assess video-text alignment) and a temporal consistency score (to measure the smoothness and coherence across frames).

The second missing ablation study focuses on the dependency noise model—specifically, its two-stage noise search algorithm. While the paper introduces a random search phase followed by a linear (fine) search phase to produce a dependency noise sequence that better preserves semantic information, it does not compare this approach against simpler alternatives. A useful ablation would involve replacing the two-stage search with a single-stage (pure random sampling) approach or even an analytical initialization based solely on the KL divergence without iterative refinement. Measuring the resulting CLIP scores and a video coherence metric (or temporal consistency) would allow one to assess the importance of the two-stage noise search in achieving high quality, temporally consistent video generation.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Temporal Momentum Attention Ablation
- **Ablated Part**: Temporal Momentum Attention (TMA) module that balances self-attention and cross-frame attention
- **Action**: REPLACE
- **Replacement**: 
  - Pure Self-Attention (µ=0)
  - Pure Cross-Frame Attention (µ=1)
  - TMA with µ values: 0.6, 0.8, 0.98
- **Metrics**: CLIP Score, Temporal Consistency Score

### Two-Stage Dependency Noise Model Ablation
- **Ablated Part**: Two-stage noise search algorithm in the dependency noise model
- **Action**: REPLACE
- **Replacement**: 
  - Single-Stage Random Noise Sampling
  - Direct Analytical KL-based Noise Initialization
- **Metrics**: CLIP Score, Video Coherence Metric

</div>