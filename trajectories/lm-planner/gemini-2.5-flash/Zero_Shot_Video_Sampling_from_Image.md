<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Zero_Shot_Video_Sampling_from_Image

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Zero-Shot Video Sampling from Image (ZS^2)" proposes a novel zero-shot video generation method from pre-trained image diffusion models. The core technical contributions are the Dependency Noise Model (DNM) and Temporal Momentum Attention (TMA).

The paper includes comparisons with baseline methods like DDIM (which samples independent images) and Text2Video-Zero. It also analyzes the effect of the hyperparameters (λ and µ) of DNM and TMA, respectively, and compares the proposed DNM qualitatively with other noise models (Mixed and Progressive). However, the paper lacks direct ablation studies that isolate the contribution of the two main proposed components, DNM and TMA, by comparing the full ZS^2 method to variants where one of these components is replaced by a simpler or standard alternative *within the ZS^2 framework*.

Specifically, the paper claims DNM ensures content consistency by introducing noise correlation, but it doesn't show how ZS^2 performs if standard i.i.d. noise (like in per-frame DDIM) is used instead of DNM while keeping TMA. This ablation would quantify the benefit of the dependency noise initialization.

Similarly, TMA is introduced to balance self-attention and cross-frame attention for animation coherence. The paper defines TMA such that setting the momentum parameter µ to 0 results in self-attention (SA) and setting it to 1 results in cross-frame attention (CFA). While the paper qualitatively compares to Text2Video-Zero (which uses CFA), it does not provide a direct ablation comparing ZS^2 with TMA (using the default µ=0.98) against ZS^2 using SA (TMA with µ=0) or ZS^2 using CFA (TMA with µ=1). This ablation would demonstrate the effectiveness of the momentum approach compared to these simpler attention mechanisms in the context of ZS^2.

Therefore, the two most important missing ablations are:
1.  Replacing the Dependency Noise Model with standard i.i.d. Gaussian noise.
2.  Replacing the Temporal Momentum Attention with standard Self-Attention and Cross-Frame Attention.

These ablations would provide quantitative evidence for the necessity and effectiveness of the proposed DNM and TMA components, respectively, which are central to the ZS^2 method's performance. The relevant metrics used in the paper are the CLIP score for quantitative evaluation and qualitative assessment of video quality, continuity, and motion coherence.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Dependency Noise Model
- **Ablated Part**: Dependency Noise Model
- **Action**: REPLACE
- **Replacement**: 
  - Standard i.i.d. Gaussian noise initialization
- **Metrics**: CLIP score, Qualitative assessment

### Ablation: Temporal Momentum Attention
- **Ablated Part**: Temporal Momentum Attention
- **Action**: REPLACE
- **Replacement**: 
  - Temporal Momentum Attention with mu=0 (Self-Attention)
  - Temporal Momentum Attention with mu=1 (Cross-Frame Attention)
- **Metrics**: CLIP score, Qualitative assessment

</div>