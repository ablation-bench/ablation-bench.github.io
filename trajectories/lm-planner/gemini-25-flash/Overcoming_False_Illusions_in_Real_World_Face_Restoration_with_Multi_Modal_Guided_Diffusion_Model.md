<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Overcoming_False_Illusions_in_Real_World_Face_Restoration_with_Multi_Modal_Guided_Diffusion_Model

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces Multi-modal Guided Real-World Face Restoration (MGFR), a diffusion-based method leveraging attribute text prompts, high-quality reference images, and identity information for face restoration. Key components include a dual-control adapter (DCA) with an LQ Control Adapter (LCA) and a Reference Control Adapter (RCA), a two-stage training strategy, and the use of negative samples/prompts for Classifier-Free Guidance (CFG).

The paper presents several ablation studies:
1.  **Training Data Volume:** Shows performance decreases with fewer training samples (Table 6).
2.  **Attribute Prompts and Negative Samples:** Evaluates the impact of positive attribute prompts, negative quality prompts, and negative attribute prompts using quantitative metrics (Table 4) and qualitative examples (Figure 13).
3.  **Additional Information Exchange:** Studies the effect of information flow links within the adapter architecture (Table 3).
4.  **Arcface Identity Embedding:** Qualitatively demonstrates the importance of identity embedding for reducing false identity illusions (Figure 15).
5.  **Reference Image Guidance:** Compares the Stage 1 model (text-guided, "w/o Reference Image") with the Stage 2 model (multi-modal guided, "MGBFR(Ours)") qualitatively (Figure 1a, 6, 28) and quantitatively (Table 1 vs Table 2), showing the combined benefit of reference and identity information.
6.  **Single vs. Dual Control Adapter:** Qualitatively compares SCA and DCA for multi-modal input (Figure 32).
7.  **CFG Hyperparameters:** Shows the qualitative influence of λna and λnq (Figure 27).

While the paper explores the impact of different prompts and adapter connections, and shows the overall benefit of adding reference/identity information, there are two important aspects that are not fully ablated or quantified:

1.  **Quantitative Impact of Arcface Identity Embedding:** The paper shows qualitatively in Figure 15 that removing the Arcface identity embedding leads to false identity illusions. However, it does not provide quantitative metrics (especially the ID metric) for this specific ablation case in the main results tables (like Table 2). Quantifying this effect would provide stronger evidence for the contribution of the identity embedding, separate from the visual features of the reference image.
2.  **Justification of the Two-Stage Training Strategy:** The paper states that the two-stage training strategy is designed to effectively utilize complex multi-modal information, implying that training the full model end-to-end might be less effective. However, no experimental comparison is provided to support this claim. An ablation comparing the performance of the model trained with the proposed two-stage strategy versus a single-stage end-to-end training would be crucial to validate this design choice.

These two missing ablations are significant because they pertain to core components and architectural/training decisions of the proposed MGFR method. Quantifying the impact of the identity embedding isolates the contribution of this specific modality, and comparing training strategies validates the chosen training approach.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Quantitative Ablation of Identity Embedding
- **Ablated Part**: Arcface identity embedding input to the Reference Control Adapter (RCA)
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, LPIPS, ManIQA, ClipIQA, MUSIQ, ID

### Ablation of Two-Stage Training
- **Ablated Part**: Two-stage training strategy
- **Action**: REPLACE
- **Replacement**: 
  - Single-stage end-to-end training
- **Metrics**: PSNR, SSIM, LPIPS, ManIQA, ClipIQA, MUSIQ, ID

</div>