<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Masked_Diffusion_Models_are_Fast_Distribution_Learners

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Masked Diffusion Models are Fast Distribution Learners" proposes a two-stage training framework for diffusion models, consisting of a masked pre-training stage followed by a standard denoising fine-tuning stage. The core idea is to use masked denoising score matching (MDSM) during pre-training to learn a "primer" distribution by modeling marginals of the data distribution, which accelerates subsequent fine-tuning on the full distribution. The method incorporates masking strategies (patch-wise, block-wise, cropping) and adds positional information of visible pixels to the input.

The paper includes several ablation studies:
1.  **Mask Configuration Investigation (Sec 4.2):** Compares different mask types (patch-wise, block-wise, cropping), mask rates (10%, 50%, 90%), block sizes, and their interaction with batch size and training steps on CelebA 64x64, measured by FID.
2.  **Unstable Pre-training Investigation (Appendix C):** Analyzes factors affecting training stability at high mask rates (90%), including batch size, learning rate, noise schedule, gradient clipping, and warmup, primarily focusing on loss/FID curves during training.
3.  **Generalizability (Sec 4.4):** Evaluates the pre-trained model's performance when fine-tuned on different training paradigms (DDPM vs. SDE/VPCosine), different datasets (CelebA -> FFHQ/AFHQ), and limited data settings, measured by FID.

While these ablations cover important aspects like mask parameters and generalizability, there are two key components/design choices that are not explicitly ablated, which would further clarify the contribution of the proposed method:

1.  **Ablating the Positional Information (H):** The method explicitly adds positional information H to the input before masking (Algorithm 1). This suggests H is considered important for the model to understand the spatial context of the visible pixels. However, the paper does not show an experiment where this positional information is *removed* to demonstrate its impact on performance (FID) and training efficiency.
2.  **Comparing Two-stage vs. Single-stage Masked Training:** The central claim is the benefit of the *two-stage* approach. The paper compares MaskDM (masked pre-train + unmasked fine-tune) to a standard DDPM trained from scratch (unmasked end-to-end). A missing comparison is against a model trained *end-to-end* using the *masked* denoising score matching (MDSM) objective for the entire training duration. This would directly test whether the separation into a distinct masked pre-training phase followed by an unmasked fine-tuning phase is crucial, or if simply training with the MDSM objective throughout provides similar benefits.

These two missing ablations are important because they directly probe the necessity of specific input modifications (positional info) and the core structural design (two-stage vs. single-stage masked training) of the proposed MaskDM framework.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablate Positional Information H
- **Ablated Part**: Addition of positional information H to the input before masking in the masked pre-training stage.
- **Action**: REMOVE
- **Metrics**: FID, Training Time (GPU Days)

### Single-stage Masked Training
- **Ablated Part**: Two-stage training framework (masked pre-training + denoising fine-tuning)
- **Action**: REPLACE
- **Replacement**: 
  - Single-stage training using the Masked Denoising Score Matching (MDSM) objective (Eq. 2) for the total training duration.
- **Metrics**: FID, Training Time (GPU Days)

</div>