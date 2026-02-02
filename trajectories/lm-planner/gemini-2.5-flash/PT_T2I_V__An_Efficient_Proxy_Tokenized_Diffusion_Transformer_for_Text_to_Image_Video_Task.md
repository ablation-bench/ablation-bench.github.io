<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/PT_T2I_V__An_Efficient_Proxy_Tokenized_Diffusion_Transformer_for_Text_to_Image_Video_Task

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "PT-T2I/V: An Efficient Proxy-Tokenized Diffusion Transformer for Text-to-Image/Video-Task" proposes PT-DiT, an efficient Diffusion Transformer architecture. The core ideas are the Proxy-Tokenized mechanism (Global Information Interaction Module - GIIM) for efficient global attention using sparse proxy tokens derived from window averaging, and the Texture Complement Module (TCM) using window and shift-window attention for local detail.

The paper includes several ablation studies in Section 4.5 and Appendix A.3:
1.  **Major Component Ablation:** Removing GIIM, TCM, or Shift-Window Attention (SWA) to show their importance (Table 2a, Fig 8).
2.  **Proxy Token Extraction Method:** Comparing averaging, top-left, and random selection for generating proxy tokens (Table 2b).
3.  **Global Information Injection Method:** Comparing Cross-Attention, Interpolation, and Linear projection for propagating proxy token information to all tokens (Table 2c).
4.  **Spatial Compression Ratio:** Evaluating different spatial compression ratios (p_h, p_w) at a fixed resolution (256) for image generation (Table 2d).
5.  **Performance and Efficiency Comparisons:** Comparing PT-DiT against other methods like DiT, SiT, and DAM in terms of FID and GFLOPs (Fig 9, Fig 10, Fig 7).

While these ablations cover key aspects like the necessity of the main modules, how proxy tokens are formed, how their information is used, and the impact of spatial compression, there are a couple of important design choices and hyperparameters that could benefit from further investigation through ablation:

1.  **Order of GIIM and TCM:** The paper presents the PT-Block with GIIM followed by TCM (Fig 4). This sequential design implies a specific flow of information (global context first, then local refinement). An ablation studying the reverse order (TCM then GIIM) would help understand if this specific order is optimal or if the interaction itself is what matters, regardless of sequence. This tests a fundamental architectural decision within the proposed block.
2.  **Temporal Compression Ratio (p_f) for Video:** The paper highlights the efficiency gains for video generation by compressing across the temporal dimension (p_f=4). While they ablate spatial compression ratios for images, they fix the temporal ratio for video. Ablating different temporal compression ratios (e.g., p_f=2, 8) would directly quantify the trade-off between temporal efficiency and video generation quality, which is crucial for understanding the video-specific contribution and scalability.

Both of these ablations are important for fully understanding the PT-DiT architecture and its application to video. The temporal compression ratio is perhaps slightly more specific to the paper's claim about efficient video generation through 3D compression. Therefore, I will suggest these two ablations, prioritizing the temporal compression ratio slightly.

The metrics used in the paper for ablations on the small model (PT-DiT/S-Class) are FID-50k. For video evaluation, they use FVD, IS, FID, and CLIPSIM, along with efficiency metrics (GFLOPs, GPU Memory). I will use these relevant metrics for the suggested ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Temporal Compression Ratio (p_f)
- **Ablated Part**: Temporal compression ratio (p_f) for video generation in the Proxy-Tokenized mechanism.
- **Action**: REPLACE
- **Replacement**: 
  - 2
  - 4
  - 8
- **Metrics**: FVD, IS, FID, CLIPSIM, GFLOPs, GPU Memory

### GIIM and TCM Order
- **Ablated Part**: Order of the Global Information Interaction Module (GIIM) and Texture Complement Module (TCM) within the PT-Block.
- **Action**: REPLACE
- **Replacement**: 
  - GIIM -> TCM
  - TCM -> GIIM
- **Metrics**: FID-50k

</div>