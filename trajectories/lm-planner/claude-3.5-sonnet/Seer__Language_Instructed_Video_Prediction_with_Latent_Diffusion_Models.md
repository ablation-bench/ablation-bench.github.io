<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Seer__Language_Instructed_Video_Prediction_with_Latent_Diffusion_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice two important missing ablation studies that could help better understand the contribution of key components:

1. The Frame Sequential Text Decomposer (FSText) is a novel and important component, but there's no ablation comparing it to simpler text encoding approaches. While they show ablations of components within FSText (temporal and sequential attention), they don't compare against a baseline that uses a single global text embedding for all frames.

2. The paper uses a pre-trained Stable Diffusion model and inflates it to 3D, but doesn't fully explore the impact of different initialization strategies for the temporal components. While they ablate fine-tuning settings, they don't examine how different ways of initializing the new temporal layers affect performance.

The metrics used in the paper are primarily FVD (Fréchet Video Distance) and KVD (Kernel Video Distance) on the Something Something V2 dataset, so these should be used for consistency.

I'll suggest these two ablations in order of importance:
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Global vs Sequential Text Embedding
- **Ablated Part**: Frame Sequential Text Decomposer
- **Action**: REPLACE
- **Replacement**: 
  - Single global CLIP embedding for all frames
  - Frame-wise CLIP embeddings without temporal decomposition
- **Metrics**: FVD, KVD

### Temporal Layer Initialization
- **Ablated Part**: Initialization of temporal attention layers
- **Action**: REPLACE
- **Replacement**: 
  - Random initialization
  - Inflation from spatial attention weights
  - Zero initialization
- **Metrics**: FVD, KVD

</div>