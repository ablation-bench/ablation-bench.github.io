<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Animate_Your_Thoughts__Reconstruction_of_Dynamic_Natural_Vision_from_Human_Brain_Activity

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Animate Your Thoughts: Reconstruction of Dynamic Natural Vision from Human Brain Activity" presents a two-stage model named Mind-Animator for reconstructing dynamic natural vision from human brain activity. The model decouples semantic, structure, and motion features from fMRI and integrates them into videos using an inflated Stable Diffusion. The paper demonstrates the effectiveness of the model through extensive experiments on multiple video-fMRI datasets.

To further evaluate the model, we suggest two missing ablation studies:

1. Ablation study on the effect of different semantic decoders: The paper uses a three-layer MLP as the semantic decoder. It would be interesting to see how different architectures, such as a transformer-based decoder, affect the performance of the model.
2. Ablation study on the effect of different motion generators: The paper uses a Consistency Motion Generator with Sparse Causal Attention. It would be interesting to see how different motion generators, such as a simple MLP or a more complex graph-based model, affect the performance of the model.

These ablation studies can provide further insights into the strengths and weaknesses of the Mind-Animator model and help identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: semantic decoder
- **Action**: REPLACE
- **Replacement**: 
  - transformer-based decoder
  - LSTM-based decoder
- **Metrics**: 2-way-I, 2-way-V, VIFI-score, SSIM, PSNR, Hue-pcc, CLIP-pcc, EPE

### Ablation B
- **Ablated Part**: motion generator
- **Action**: REPLACE
- **Replacement**: 
  - simple MLP
  - graph-based model
- **Metrics**: 2-way-I, 2-way-V, VIFI-score, SSIM, PSNR, Hue-pcc, CLIP-pcc, EPE

</div>