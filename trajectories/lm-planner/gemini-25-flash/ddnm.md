<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/ddnm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user requested up to 5 ablation study suggestions for the paper "Zero-Shot Image Restoration Using Denoising Diffusion Null-Space Model". The goal is to identify key components of the proposed DDNM and DDNM+ methods and suggest experiments to evaluate their contribution or sensitivity. The suggestions should be ranked by importance and formatted as a JSONL output.

I have analyzed the paper, focusing on the method section (Section 3) and the experimental results (Section 4). The core of the method is the Denoising Diffusion Null-Space Model (DDNM), which leverages the range-null space decomposition and refines only the null-space during the reverse diffusion process (Eq. 10). The enhanced version, DDNM+, adds scaling for noisy inputs (Eq. 11, 12) and a time-travel trick for improved quality (Algorithm 2).

The paper already presents some comparisons that function as ablations:
- DDNM vs. baseline methods (Table 1, 2): Shows the overall effectiveness of DDNM.
- DDNM+ vs. DDNM on noisy data (Table 3): Shows the benefit of the DDNM+ enhancements for noisy inputs.
- DDNM+ vs. DDNM+ w/o time-travel on noisy data (Table 3): Specifically shows the benefit of the time-travel trick on noisy SR.
- Visual results for different time-travel lengths $l$ (Fig 3(b)).

Based on this, I will propose ablation studies that explore aspects not fully covered in the main paper's experiments:

1.  **Compare Projection Strategy:** The paper's core is projecting the *estimated clean image* $\mathbf{x}_{0|t}$ onto the data consistency manifold. A common alternative in diffusion-based inverse problems is to project the *noisy intermediate sample* $\mathbf{x}_t$. Comparing these two fundamental strategies would highlight the specific advantage of the DDNM approach. This is a high-importance ablation.
2.  **Vary Time-Travel Parameters:** The paper shows the effect of the travel length $l$ visually and implicitly includes $l>0$ in DDNM+ quantitative results. However, the time-travel trick also involves parameters $s$ (interval) and $r$ (repeat times) (Algorithm 2 mentions $s=1, r=1$). Ablating these parameters would provide insight into the sensitivity and optimal configuration of this enhancement. This is a medium-high importance ablation.
3.  **Sensitivity to Noise Level Estimation:** DDNM+ requires manually setting the noise level $\sigma_y$ for noisy tasks. Real-world noise levels are often unknown or estimated. Evaluating the method's performance when the provided $\sigma_y$ is inaccurate is crucial for practical application. This is a medium-high importance ablation.
4.  **Compare Pseudo-inverse Implementation:** The paper mentions using hand-designed pseudo-inverses for some tasks (SR, Colorization, Inpainting) for simplicity. Comparing the performance and computational cost of these hand-designed operators against a general SVD-based pseudo-inverse computation would be valuable. This is a medium importance ablation.
5.  **Impact of Diffusion Model Prior:** The method relies heavily on the pre-trained diffusion model as a generative prior. While not an ablation of the DDNM/DDNM+ algorithm itself, evaluating performance with different pre-trained models (e.g., different architectures, training datasets) would demonstrate the generality and robustness of the approach to the choice of prior. This is a medium importance ablation.

These five ablations cover the core projection mechanism, the key DDNM+ enhancements (time-travel parameters, noise handling sensitivity), implementation details ($\mathbf{A}^{\dagger}$), and the external dependency (diffusion model). They are distinct from the main comparisons already presented in the paper. The metrics used will be consistent with the paper: PSNR, SSIM, FID, and Consistency where applicable.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Compare Projection Strategy
- **Ablated Part**: Strategy for enforcing data consistency during reverse diffusion (projecting estimated clean image x_0|t vs. projecting noisy sample x_t).
- **Action**: REPLACE
- **Replacement**: 
  - Projection on estimated clean image x_0|t (DDNM/DDNM+)
  - Projection on noisy sample x_t
- **Metrics**: PSNR, SSIM, FID, Consistency

### Vary Time-Travel Parameters
- **Ablated Part**: Time-travel parameters s (interval) and r (repeat times).
- **Action**: REPLACE
- **Replacement**: 
  - {'s': 1, 'r': 1}
  - {'s': 2, 'r': 1}
  - {'s': 5, 'r': 1}
  - {'s': 1, 'r': 2}
- **Metrics**: PSNR, SSIM, FID

### Sensitivity to Noise Level Estimation
- **Ablated Part**: Sensitivity of DDNM+ performance to the manually set noise level sigma_y for noisy tasks.
- **Action**: REPLACE
- **Replacement**: 
  - Estimated sigma_y
  - 0.75 * Estimated sigma_y
  - 1.25 * Estimated sigma_y
  - 0.5 * Estimated sigma_y
  - 1.5 * Estimated sigma_y
- **Metrics**: PSNR, SSIM, FID

### Compare Pseudo-inverse Implementation
- **Ablated Part**: Method for computing the pseudo-inverse A_dagger.
- **Action**: REPLACE
- **Replacement**: 
  - Hand-designed (as used in paper for specific tasks)
  - General SVD-based computation
- **Metrics**: PSNR, SSIM, FID, Consistency

### Impact of Diffusion Model Prior
- **Ablated Part**: The specific pre-trained diffusion model used as the generative prior.
- **Action**: REPLACE
- **Replacement**: 
  - Original pre-trained model used in paper
  - Another pre-trained diffusion model (different architecture or training data)
- **Metrics**: PSNR, SSIM, FID

</div>