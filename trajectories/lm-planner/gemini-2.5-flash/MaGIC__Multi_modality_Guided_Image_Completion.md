<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/MaGIC__Multi_modality_Guided_Image_Completion

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants me to identify and suggest up to two important missing ablation studies for the paper "MaGIC: Multi-modality Guided Image Completion".

I have analyzed the paper's abstract, method section, and existing experimental results, particularly the ablation studies presented in Section 4.4 and Appendix C.

The core components of the MaGIC method are:
1.  **Modality-specific conditional U-Net (MCU-Net):** Trained individually for each single modality, injecting guidance into a frozen pre-trained Stable Diffusion U-Net denoiser.
2.  **Consistent Modality Blending (CMB):** A training-free method combining signals from multiple trained MCU-Nets during inference via gradient guidance.

The paper already includes ablations on:
-   The impact of different single and combined modalities (Table 3a).
-   Comparing the proposed CMB with a naive Feature-Level Addition (FLA) for multi-modality blending (Table 2a).
-   Hyperparameters of the CMB inference process (P and Q) (Table 3b).
-   A comparison of the training-free MaGIC approach against a hypothetical joint multi-modality re-training approach.

Based on this analysis, two key aspects of the method that are central to its design but not thoroughly ablated are:

1.  **The training strategy for the MCU-Net:** Specifically, the decision to freeze the pre-trained U-Net denoiser and only train the lightweight encoding network. This is a crucial design choice that enables the training-free CMB, but its impact compared to fine-tuning or training the full U-Net is not directly evaluated as an ablation. While the joint re-training comparison touches upon training, it's a different system architecture (a single fuser vs. multiple MCU-Nets). An ablation on *how* the MCU-Net's U-Net part is handled during training (frozen vs. fine-tuned vs. trained) would isolate the effect of this specific strategy within the MCU-Net framework.
2.  **The modality injection mechanism within the MCU-Net:** The paper states that the modality features are injected by simple addition to the encoder's intermediate features (F_hat_l_c = F_l_enc + F_l_c). This is a specific architectural choice for incorporating the modality signal. Other common methods exist (e.g., concatenation, cross-attention, FiLM layers). An ablation comparing these different injection mechanisms would validate the chosen simple addition approach.

I will prioritize these two as they represent fundamental design decisions for the MCU-Net, which is the building block for the entire MaGIC framework.

The metrics used in the paper for quantitative evaluation include FID, PickScore, U-IDS, and P-IDS. I will use these metrics for the suggested ablations.

The first suggested ablation will investigate the freezing strategy of the U-Net denoiser during MCU-Net training. The action will be REPLACE, exploring training the full U-Net or partially fine-tuning it.

The second suggested ablation will investigate the modality injection mechanism within the MCU-Net. The action will be REPLACE, exploring alternative methods like concatenation or cross-attention.

These two ablations are important because they directly assess the impact of core architectural and training decisions of the MCU-Net, which is foundational to MaGIC's performance and flexibility.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: MCU-Net U-Net Training Strategy
- **Ablated Part**: Training strategy for the U-Net denoiser within the Modality-specific Conditional U-Net (MCU-Net)
- **Action**: REPLACE
- **Replacement**: 
  - Train the full U-Net denoiser end-to-end
  - Fine-tune the U-Net denoiser (e.g., later layers)
- **Metrics**: FID, PickScore, U-IDS, P-IDS

### Ablation: MCU-Net Modality Injection Mechanism
- **Ablated Part**: Method for injecting modality guidance features into the U-Net denoiser's intermediate features within the MCU-Net
- **Action**: REPLACE
- **Replacement**: 
  - Concatenation
  - Cross-attention
  - FiLM (Feature-wise Linear Modulation)
- **Metrics**: FID, PickScore, U-IDS, P-IDS

</div>