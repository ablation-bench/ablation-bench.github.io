<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/DuaRot__Dual_Rotation_for_Advanced_Outlier_Mitigation_in_Rotated_LLMs

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "DuaRot: Dual Rotation for Advanced Outlier Mitigation in Rotated LLMs" proposes a novel quantization method based on dual rotation matrices (Global R<sup>G</sup> and Local R<sup>L</sup>) and a hardware-aware strategy for configuring online rotation matrices (R<sup>3</sup> and R<sup>4</sup>). The method applies R<sup>G</sup> and R<sup>L</sup> sequentially during training and merges them for inference. The hardware strategy determines whether R<sup>3</sup> and R<sup>4</sup> should be trainable (Matmul) or fixed Hadamard (WHT) based on their size and hardware performance.

The paper includes several ablation studies:
1.  **Hardware-aware matrix configuration strategy and dual rotation (Table 3):** This study investigates the combined effect of the 'Dual Rotation' (R<sup>G</sup>+R<sup>L</sup> vs R<sup>G</sup> only) and the 'Hardware Strategy' for R<sup>3</sup>/R<sup>4</sup> (using the strategy vs always Hadamard). The baseline is SpinQuant, which uses trainable R<sup>1</sup>, R<sup>2</sup>, R<sup>3</sup>, R<sup>4</sup> (with R<sup>3</sup>/R<sup>4</sup> initialized as Hadamard).
2.  **Reparameterization matrix size (d for R<sup>L</sup> blocks) (Figure 5):** This ablates the block size `d` for the local rotation matrix R<sup>L</sup>, showing performance varies with `d`.
3.  **Calibration set (Table 4, 5):** This explores the impact of the training calibration dataset (WikiText-2 vs C4) on PPL and zero-shot accuracy.
4.  **Global Rotation Matrix v.s. Local Rotation Matrix (Appendix F, Figure 17):** This shows the performance of *only* the local matrix (R<sup>L</sup>) with varying block size `d`, demonstrating that larger `d` is better when R<sup>L</sup> is used alone.

While Table 3 provides an ablation of the 'Dual Rotation' component (comparing R<sup>G</sup>+R<sup>L</sup> vs R<sup>G</sup>), it does so in conjunction with the hardware strategy ablation. A more granular ablation of the "Dual Rotation" mechanism itself would be beneficial to clearly understand the individual contributions of the Global (R<sup>G</sup>) and Local (R<sup>L</sup>) components when applied sequentially, independent of the R<sup>3</sup>/R<sup>4</sup> hardware strategy. Specifically, comparing using only R<sup>G</sup>, only R<sup>L</sup> (with the optimal block size d=64 found in Figure 5), and their combination (R<sup>G</sup>+R<sup>L</sup>) would provide a clearer picture of how these two parts contribute to the overall performance gain attributed to "Dual Rotation". This is a core novelty of the paper, and a detailed breakdown is important.

Another aspect not explicitly ablated is the initialization strategy for the trainable rotation matrices. The paper mentions initializing R<sup>1</sup>, R<sup>2</sup>, R<sup>3</sup>, R<sup>4</sup> with randomized Hadamard and R<sup>L</sup> with Identity. Ablating this choice (e.g., comparing Hadamard/Identity initialization to all Identity or all Random Orthogonal initialization) would demonstrate the importance of the chosen initialization for the training process and final performance.

Based on the paper's focus and existing ablations, the most important missing studies are:
1.  A detailed breakdown of the Global vs Local components within the Dual Rotation mechanism.
2.  An ablation of the initialization strategy for the trainable rotation matrices.

These two ablations would provide deeper insights into the effectiveness of the core proposed techniques.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Dual Rotation Component Analysis
- **Ablated Part**: Individual contributions of Global (R^G) and Local (R^L) rotation matrices within the Dual Rotation mechanism
- **Action**: REPLACE
- **Replacement**: 
  - Only Global Rotation (R^G)
  - Only Local Rotation (R^L, d=64)
  - Global + Local Rotation (R^G + R^L, d=64)
- **Metrics**: WikiText-2 perplexity, Average zero-shot accuracy

### Rotation Matrix Initialization
- **Ablated Part**: Initialization strategy for trainable rotation matrices (R^G, R^L, R^2, R^3, R^4)
- **Action**: REPLACE
- **Replacement**: 
  - Randomized Hadamard (current)
  - Identity
  - Random Orthogonal
- **Metrics**: WikiText-2 perplexity, Average zero-shot accuracy

</div>