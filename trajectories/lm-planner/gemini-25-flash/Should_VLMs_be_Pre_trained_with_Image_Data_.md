<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Should_VLMs_be_Pre_trained_with_Image_Data_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Should VLMs be Pre-trained with Image Data?" investigates the optimal timing and data mix for introducing image data during VLM pre-training, challenging the traditional two-stage approach (full LLM pre-training then VLM training). The authors propose integrating image-text data earlier in the pre-training process, specifically during the cooldown phase of text-only pre-training (around 80% completion).

The paper presents several ablation studies:
1.  **Timing of image introduction:** Varying the percentage of text pre-training completed before introducing image data (Section 3.1).
2.  **Image-text ratio:** Exploring different ratios of image-text to text-only data during the mixed pre-training phase, both when starting from an 80% checkpoint (Section 3.2) and from scratch (Section 3.3).
3.  **Source of image data:** Comparing image captions vs. instruction tuning data during the mixed pre-training phase (Section 3.4).
4.  **Fine-tuning epochs:** Analyzing the impact of the number of fine-tuning epochs on downstream performance (Section 3.5).
5.  **Image dataset:** Ablating different caption datasets (Appendix J.1).
6.  **Image encoder:** Ablating different image encoder architectures (Appendix J.2).
7.  **Frozen vs. Unfrozen encoder:** Comparing training with frozen vs. unfrozen image encoder weights (Appendix I). This was done on 79M models.
8.  **Scaling:** Limited experiments on higher token multipliers (79M models, Appendix G) and a limited comparison at 7B scale (Appendix H).

Based on the paper's focus and the existing ablations, two important missing ablation studies stand out:

1.  **Frozen vs. Unfrozen Image Encoder at 1B Scale:** The paper concludes that freezing the image encoder weights is more effective (Appendix I). However, this conclusion is drawn from experiments on the smaller 79M parameter model. The main experiments and findings of the paper are presented for the 1B parameter scale. It is crucial to verify if the finding that freezing the encoder is better holds true at the 1B scale, as model behavior and optimal strategies can change with scale. This ablation would directly support or challenge a key design choice applied to the main model size studied.
2.  **Image Projection Layer Architecture:** The method uses a 2-layer MLP as the projection block between the image encoder and the language model. While this is a common approach, the specific architecture (number of layers, intermediate dimension) is a design choice that can significantly impact how visual information is integrated into the language model. The paper does not ablate this component. Comparing the default 2-layer MLP with a simpler 1-layer MLP (another common choice, e.g., in LLaVA) would help understand the importance of the projection complexity in their proposed training setup.

These two ablations address fundamental components/strategies (encoder training strategy and projection architecture) at the scale primarily investigated in the paper, providing deeper insight into the method's performance drivers.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Frozen vs Unfrozen Encoder (1B)
- **Ablated Part**: Image encoder weights (SigLIP 400M)
- **Action**: REPLACE
- **Replacement**: 
  - Frozen
  - Unfrozen
- **Metrics**: Vision Stable Score, Text Stable Score, VQAv2, ARC-easy

### Image Projection Layer Architecture
- **Ablated Part**: Architecture of the image projection block
- **Action**: REPLACE
- **Replacement**: 
  - 2-layer MLP (default)
  - 1-layer MLP
- **Metrics**: Vision Stable Score, Text Stable Score, VQAv2, ARC-easy

</div>