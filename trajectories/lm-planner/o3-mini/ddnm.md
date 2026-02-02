<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/ddnm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies that aim to isolate and quantify the contribution of each crucial component in DDNM and its enhanced version DDNM⁺. First, we study the core idea of “null‐space refinement” that reprojects the diffusion model’s estimate using the operator A† (the pseudo‐inverse) to enforce data consistency; by removing this component, we expect a drop in both consistency and overall image quality. Second, in DDNM⁺ the scaling factors (Σₜ and Φₜ) balance the range-space correction when noise is present. Replacing the proposed (noise-adaptive) scaling factors with a fixed identity scaling tests the importance of this modulation for noisy image restoration. Third, the “time-travel trick” is introduced to improve global harmony and restore better null-space details; removing it will quantify its benefit in generating perceptually coherent results. Fourth, we propose to vary the travel length parameter (l) in the time-travel trick (e.g., setting l = 0, 2, and 4) to understand how far back the model should “travel” in time to best salvage disharmonious estimates. Finally, since A and its pseudo-inverse A† can be constructed in different ways (hand-designed versus computed via SVD), we propose an ablation study on the pseudo-inverse construction method to examine its effect on restoration quality. The metrics for these studies (e.g., PSNR, SSIM, FID, and a consistency measure) match those used in the paper.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Null-Space Refinement Removal
- **Ablated Part**: The null-space refinement step that combines the pre-computed range-space (A†y) with the diffusion's estimated x₀ (via (I - A†A)x₀) to enforce data consistency.
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, FID, Consistency Error

### Scaling Range-Space Correction Ablation
- **Ablated Part**: The scaling factors (Σₜ and Φₜ) in DDNM⁺ that modulate the range-space correction A†(Ax₀|t - y) for noisy image restoration.
- **Action**: REPLACE
- **Replacement**: 
  - identity scaling (Σₜ = I, Φₜ = σₜ²I)
  - proposed noise-adaptive scaling
- **Metrics**: PSNR, SSIM, FID, Consistency Error

### Time-Travel Trick Removal
- **Ablated Part**: The time-travel trick designed to refine past state estimates by temporarily moving to a later diffusion timestep and then reverting (improving global consistency).
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, FID, Consistency Error

### Varying Time-Travel Length
- **Ablated Part**: The time-travel parameter (l) controlling how far back in time the diffusion process is re-initialized to improve null-space estimation.
- **Action**: REPLACE
- **Replacement**: 
  - 0
  - 2
  - 4
- **Metrics**: PSNR, SSIM, FID

### Pseudo-Inverse Construction Method
- **Ablated Part**: The design of the pseudo-inverse A† used in enforcing data consistency, comparing hand-designed operators with SVD-based computed pseudo-inverses.
- **Action**: REPLACE
- **Replacement**: 
  - hand-designed operator
  - SVD-based operator
- **Metrics**: PSNR, SSIM, FID

</div>