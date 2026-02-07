<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Unpacking_SDXL_Turbo__Interpreting_Text_to_Image_Models_with_Sparse_Autoencoders

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Unpacking SDXL Turbo: Interpreting Text-to-Image Models with Sparse Autoencoders" proposes using Sparse Autoencoders (SAEs) to interpret the intermediate representations of SDXL Turbo, specifically focusing on the residual updates of selected transformer blocks within the U-net. The authors train SAEs on $\Delta D_{ij} = D^{out}_{ij} - D^{in}_{ij}$, the difference between the output and input of these blocks, arguing that this represents the block's contribution. They select four blocks (down.2.1, mid.0, up.0.0, up.0.1) based on a qualitative assessment of their impact when ablated (Appendix C). They then analyze the learned features qualitatively through visualizations and quantitatively using metrics like CLIP similarity for specificity, texture relatedness, color sensitivity, and intervention locality. They also evaluate SAE reconstruction quality (Appendix D).

The paper includes several ablation-like experiments:
1.  Ablating individual transformer blocks to select targets for SAE training (Appendix C).
2.  Evaluating the reconstruction quality of the trained SAEs by replacing the original residual update with the SAE reconstruction (Appendix D).
3.  Performing feature-level interventions (ablation/enhancement) to demonstrate causality (Section 4 & 5).

Based on the method and existing experiments, two important missing ablation studies stand out:

1.  **Choice of Intermediate Representation:** The core method trains SAEs on the *residual update* ($\Delta D$). It is not explicitly shown why this is the optimal or necessary representation compared to training on the block's raw output ($D^{out}$) or input ($D^{in}$). An ablation studying the impact of training SAEs on these different representations would validate the choice of $\Delta D$ and provide insight into where interpretable features are best captured within the block's computation.
2.  **Generalizability to Low-Impact Blocks:** The authors select blocks with "relatively high impact" for SAE training. While they show features are interpretable in these blocks, it's unclear if the method works equally well or differently on blocks with lower perceived impact (as seen in Appendix C, Fig 3). Training an SAE on a block identified as having low impact and comparing its features to those from a high-impact block would test the generalizability of the approach and quantify the difference in interpretability or causal effect across layers.

I will suggest these two ablations, prioritizing the first one as it directly questions a fundamental design choice of the method. The metrics used for evaluation should align with those already presented in the paper where possible, focusing on interpretability, causality, and reconstruction quality.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### SAE Training Target Ablation
- **Ablated Part**: Intermediate representation used for training Sparse Autoencoders (SAEs)
- **Action**: REPLACE
- **Replacement**: 
  - Block Output (D_out)
  - Block Input (D_in)
- **Metrics**: Specificity (CLIP Similarity), Relatedness to Texture (CLIP Similarity), Color Sensitivity (Manhattan Distance), Intervention Locality (Manhattan Distance), Reconstruction LPIPS, Explained Variance Ratio, Qualitative Feature Analysis

### Low-Impact Block Ablation
- **Ablated Part**: Training Sparse Autoencoders (SAEs) only on high-impact transformer blocks
- **Action**: ADD
- **Replacement**: 
  - SAE trained on a low-impact transformer block (e.g., down.0.0)
- **Metrics**: Specificity (CLIP Similarity), Relatedness to Texture (CLIP Similarity), Color Sensitivity (Manhattan Distance), Intervention Locality (Manhattan Distance), Reconstruction LPIPS, Explained Variance Ratio, Qualitative Feature Analysis

</div>