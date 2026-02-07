<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Guiding_Instruction_based_Image_Editing_via_Multimodal_Large_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I'll suggest missing ablation studies focusing on the major components of the MGIE method. Let me first summarize the existing ablations from Table 3 in the paper:

1. The paper ablates different architectures to use expressive instructions:
- FZ (Frozen): Using derived expressive instructions as input to frozen InsPix2Pix
- FT (Fine-tuning): Fine-tuning InsPix2Pix to adapt to expressive instructions
- E2E (End-to-end): Their proposed approach

However, there are some important components that weren't ablated:

1. The Visual Tokens Component: The paper uses N=8 [IMG] tokens appended after the expressive instructions E, but doesn't investigate the impact of this design choice. This is a crucial architectural decision that deserves investigation.

2. The Edit Head Architecture: The edit head T is described as a "sequence-to-sequence model" that transforms visual tokens to semantic latents, but its specific architecture (4-layer Transformer) isn't validated through ablations.

Given the importance of these components and their direct impact on the method's performance, I'll suggest ablation studies for them, ranked by importance:
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Visual Tokens Ablation
- **Ablated Part**: Number of [IMG] tokens appended after expressive instructions
- **Action**: REPLACE
- **Replacement**: 
  - 4
  - 16
  - 32
- **Metrics**: L1, DINO, CVS, SSIM, LPIPS

### Edit Head Architecture Ablation
- **Ablated Part**: 4-layer Transformer architecture of the edit head T
- **Action**: REPLACE
- **Replacement**: 
  - 2-layer Transformer
  - 6-layer Transformer
  - MLP architecture
- **Metrics**: L1, DINO, CVS, SSIM, LPIPS

</div>