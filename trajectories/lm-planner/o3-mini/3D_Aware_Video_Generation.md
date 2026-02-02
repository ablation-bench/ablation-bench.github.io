<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/3D_Aware_Video_Generation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Our review of the paper shows that the authors perform ablations on several key design choices such as the background NeRF versus static/dynamic separation, the incorporation of motion via a dedicated motion generator (including different ways of integrating time), and the use of separate image and video discriminators. However, two important aspects remain untested. First, the model relies on two independent latent codes – one for 3D content and one for motion. While qualitative results illustrate that using independent latent spaces aids in decomposing content and motion (as seen in Figure 6), the paper does not experimentally ablate this design choice. A missing study would be to replace the independently sampled latent vectors with a single shared latent vector, in order to quantify the benefit of the disentanglement on the quality and controllability (using metrics such as FVD, FID, ACD, CPBD, and view-consistent identity scores). 

Second, the method hinges on sampling diverse camera viewpoints from a dataset-dependent distribution to achieve multi-view consistency. Although the architecture is designed and justified by sampling varying camera extrinsics, no ablation is provided to measure what happens if camera viewpoints are not varied (for example, using a fixed canonical viewpoint rather than a sampled one). This experiment would verify how crucial random viewpoint sampling is for learning accurate 3D representations that can be manipulated across views.

These two proposed ablations address core components of the system that significantly contribute to its performance and controllability.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A: Latent Code Factorization
- **Ablated Part**: Independent latent spaces for 3D content and motion
- **Action**: REPLACE
- **Replacement**: 
  - shared latent code
- **Metrics**: FVD, FID, ACD, CPBD, ID

### Ablation B: Camera Viewpoint Sampling
- **Ablated Part**: Diverse camera extrinsics sampling during training
- **Action**: REPLACE
- **Replacement**: 
  - fixed canonical viewpoint
  - random sampled viewpoints
- **Metrics**: FVD, FID, ACD, CPBD, ID

</div>