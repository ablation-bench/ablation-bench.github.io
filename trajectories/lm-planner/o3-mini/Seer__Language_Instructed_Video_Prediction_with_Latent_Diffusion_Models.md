<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Seer__Language_Instructed_Video_Prediction_with_Latent_Diffusion_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two missing ablation studies that target the core contributions of Seer. First, while the paper extensively evaluates the impact of different temporal attention mechanisms and the initialization of the FSText Decomposer, it does not compare against a baseline that omits the fine-grained language decomposition entirely. Removing the FSText module and simply duplicating the global CLIP text embedding for each frame would help quantify the benefit of the decomposer in achieving temporal text-video alignment, as measured by FVD and KVD. Second, although the FSText module produces one sub‐instruction per frame, the effect of varying the granularity of language decomposition has not been systematically studied. Replacing the per-frame sub‐instruction design with coarser decompositions (e.g. one token per 2 frames or per 4 frames) can reveal whether the fine-grained guidance is critical for maintaining temporal coherence and high fidelity in video generation. Both ablations would offer insight into the importance of the language conditioning design.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Remove FSText Decomposer
- **Ablated Part**: Frame Sequential Text Decomposer module that converts a global instruction into frame-wise sub-instructions
- **Action**: REMOVE
- **Metrics**: FVD, KVD

### Sub-instruction Granularity Ablation
- **Ablated Part**: Temporal granularity of sub-instruction tokens produced by the FSText Decomposer
- **Action**: REPLACE
- **Replacement**: 
  - per-frame
  - per-2-frames
  - per-4-frames
- **Metrics**: FVD, KVD

</div>