<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/dit

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose four key ablation studies. The first targets the conditioning mechanism in transformer blocks, which is central to the DiT design. By comparing in-context conditioning, cross‐attention, adaptive layer norm (adaLN), and its variant adaLN-Zero, we can quantify how the method of incorporating conditional inputs (e.g., time and class embeddings) influences final generative performance (measured by FID-50K) as well as the computational overhead (measured by Gflops). The second study focuses on the patchify stage: varying the patch size (e.g., 2, 4, or 8) changes the number of input tokens and therefore the model’s computational complexity, while potentially affecting image quality. The third study examines the model scaling strategy by trading off transformer depth and width while roughly controlling for Gflops. This will help determine if a deeper-narrower or a shallower-wider design produces better FID scores under a constrained compute budget. Finally, the fourth ablation tests the decoder architecture. Although a simple linear decoder is used in the paper, exploring alternatives such as an MLP or a convolutional decoder may yield insights into decoding quality of the latent tokens, with FID-50K as a key metric.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Conditioning Methods
- **Ablated Part**: Transformer block conditioning mechanism
- **Action**: REPLACE
- **Replacement**: 
  - in-context conditioning
  - cross-attention
  - adaptive layer norm (adaLN)
  - adaLN-Zero
- **Metrics**: FID-50K, Gflops

### Ablation 2: Patch Size
- **Ablated Part**: Patchify layer hyperparameter (patch size)
- **Action**: REPLACE
- **Replacement**: 
  - 2
  - 4
  - 8
- **Metrics**: FID-50K, Gflops

### Ablation 3: Depth vs. Width Trade-off
- **Ablated Part**: Transformer backbone scaling (trading off depth vs. hidden dimension width)
- **Action**: REPLACE
- **Replacement**: 
  - deeper-narrower configuration
  - shallower-wider configuration
- **Metrics**: FID-50K, Gflops

### Ablation 4: Decoder Architecture
- **Ablated Part**: Decoder mapping from token sequence to latent/noise prediction
- **Action**: REPLACE
- **Replacement**: 
  - standard linear decoder
  - MLP decoder
  - convolutional decoder
- **Metrics**: FID-50K

</div>