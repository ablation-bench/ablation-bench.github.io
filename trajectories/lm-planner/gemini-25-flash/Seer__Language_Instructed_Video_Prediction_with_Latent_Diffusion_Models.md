<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Seer__Language_Instructed_Video_Prediction_with_Latent_Diffusion_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Seer: Language Instructed Video Prediction with Latent Diffusion Models" proposes an efficient method for text-conditioned video prediction by inflating a pretrained text-to-image (T2I) diffusion model. The core components include an Inflated 3D U-Net with computation-efficient spatial-temporal attention and a novel Frame Sequential Text (FSText) Decomposer that provides temporally aligned sub-instructions. A key design choice is freezing most of the pretrained 2D U-Net layers and only fine-tuning the newly added temporal attention layers and the FSText Decomposer. The method also conditions the prediction on initial reference frames.

The paper includes several ablation studies in Section 5.5 and Appendix B.5:
1.  Comparison of different temporal attention mechanisms (SAWT-Atten vs. others).
2.  Ablation on the initialization strategy for the FSText Decomposer (identity vs. random).
3.  Ablation on which parts of the U-Net and FSText Decomposer are fine-tuned (default setting vs. fine-tuning only temporal attention, or temporal + spatial-cross attention, with/without FSText).
4.  Ablation on the layer depth of the FSText Decomposer.
5.  Ablation on the components within the FSText Decomposer (temporal attention, text-sequential attention).
6.  Visual analysis comparing frame-wise sub-instructions to constant ones.

While these ablations cover important aspects like the FSText Decomposer design and the type of temporal attention, there are two significant design choices whose impact on performance is not fully explored through dedicated ablation studies:

1.  **The role of Reference Frames:** The task is Text-conditioned *Video Prediction*, explicitly stating conditioning on initial frames. The paper uses 2 reference frames for SSv2 and 1 for other datasets. However, there is no ablation study investigating the effect of using a different number of reference frames (e.g., 0, 1, 2, or more) on the prediction quality and temporal consistency. Understanding the contribution of the reference frames and how the number of frames impacts performance is crucial for a prediction task.

2.  **The impact of Freezing Pretrained 2D Layers:** A core claim is the efficiency and effectiveness of freezing the majority of the pretrained 2D U-Net layers and only training the temporal layers and FSText. While Table 4 shows that training spatial-cross attention *along with* temporal attention and FSText performs poorly, this doesn't directly isolate the benefit of *freezing* the 2D spatial layers compared to training them. A direct comparison between the default strategy (freezing 2D spatial layers, training temporal attention + FSText) and a setting where the 2D spatial layers are also fine-tuned would quantify the performance gain (or loss) attributed to this freezing strategy, beyond just efficiency benefits shown in Tables 8 and 9.

Based on their importance to the core method and the task (prediction based on initial frames, leveraging pretrained models efficiently), these two missing ablations are the most critical to suggest. The standard machine evaluation metrics used in the paper (FVD and KVD) are appropriate for these studies.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Number of Reference Frames
- **Ablated Part**: Number of reference frames used for conditioning the video prediction.
- **Action**: REPLACE
- **Replacement**: 
  - 0
  - 1
  - 2
- **Metrics**: FVD↓, KVD↓

### Ablation: Freezing 2D Spatial Layers
- **Ablated Part**: Strategy for training or freezing the pretrained 2D spatial layers (ResNet blocks, Spatial Attention blocks) in the U-Net.
- **Action**: REPLACE
- **Replacement**: 
  - Freeze 2D Spatial Layers (Default)
  - Fine-tune 2D Spatial Layers
- **Metrics**: FVD↓, KVD↓

</div>