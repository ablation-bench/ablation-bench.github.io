<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Privacy_Preserving_Vision_Transformer_on_Permutation_Encrypted_Images

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a privacy-preserving learning paradigm using permutation-based encryption strategies (Random Shuffling - RS and Mixing-up - MI) and adapted Vision Transformers (PEViT for classification on RS, PEYOLOS for detection on MI).

The paper includes several ablation studies:
1.  **Impact of RPE:** Compares PEViT with and without Reference-Based Positional Encoding (RPE) for image classification on RS-encrypted images (Appendix B, Table 3).
2.  **Impact of Patch Size:** Investigates different patch sizes for PEYOLOS on MI-encrypted images for object detection (Appendix C, Table 5). This is an ablation on a parameter of the encryption strategy (patch size for initial decomposition) in the context of a specific task and model.
3.  **Impact of Nonlinear Embedding ($\mathcal{H}$):** Compares different complexities of the mapping function $\mathcal{H}$ used in PEYOLOS for MI-encrypted patches (Appendix C, Table 6).
4.  **Impact of Encryption Parameters on Attack/Performance:** Explores how patch size, interval, drop ratio, and image size affect the success of puzzle solver attacks and classification performance on RS-encrypted images (Section 4.4, Appendix E, Figures 4, 5, 16).

Based on the method description and existing ablations, here are two important missing ablation studies:

1.  **Impact of MI Sub-patch Grid Size:** The Mixing-up (MI) strategy involves decomposing image patches into sub-patches and mixing them (Eq 1). For PEYOLOS, the paper specifies using 4 sub-patches (a 2x2 grid within the patch) (Sec 3.4). The number or arrangement of these sub-patches (the grid size) is a parameter of the MI encryption that likely affects both the degree of privacy protection (more sub-patches = more mixing) and the amount of machine-learnable information preserved. An ablation varying this parameter would be crucial to understanding the trade-off and optimal configuration for MI. The paper ablates the initial patch size (Table 5), but not the sub-patch decomposition *within* that patch for MI.
2.  **PEViT vs. Standard ViT on MI Encryption:** The paper designs PEViT specifically for RS (permutation-equivariant). MI, however, preserves some positional information by mixing *within* patches but keeping the patch order. Table 1 shows results for DeiT-B (a standard ViT with positional encoding) on MI-encrypted images (78.0% top-1 acc) and PEViT-B (without RPE, permutation-equivariant) on RS-encrypted images (78.7%). A direct comparison of PEViT-B (without RPE) trained on MI-encrypted images versus DeiT-B trained on MI-encrypted images is missing. This would clarify whether the permutation-equivariant design of PEViT is beneficial, detrimental, or neutral when applied to MI-encrypted data, which has different positional properties than RS-encrypted data.

I will prioritize the ablation on the MI sub-patch grid size as it directly investigates a core parameter of one of the proposed encryption methods. The second ablation clarifies the interaction between the model design and the MI encryption strategy.

The metrics used in the paper are ImageNet top-1 accuracy for classification and COCO AP for object detection. These should be used for the respective tasks in the proposed ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Impact of MI Sub-patch Grid Size
- **Ablated Part**: Grid size for sub-patch decomposition within each patch in the Mixing-up (MI) encryption strategy.
- **Action**: REPLACE
- **Replacement**: 
  - 1x1 (no mixing)
  - 2x2 (current)
  - 4x4
- **Metrics**: AP

### PEViT vs. Standard ViT on MI Encryption
- **Ablated Part**: Model architecture (Permutation-Equivariant ViT vs. standard ViT with positional encoding) when trained on MI-encrypted images.
- **Action**: REPLACE
- **Replacement**: 
  - PEViT (without RPE)
  - Standard ViT (e.g., DeiT-B)
- **Metrics**: top-1 acc.

</div>