<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Pose_Modulated_Avatars_from_Video

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Pose Modulated Avatars from Video" introduces a novel approach to reconstruct dynamic human motion and shape using Neural Radiance Fields (NeRF) driven by an underlying skeleton. The method is characterized by a two-branch neural network that operates in the frequency domain, with one branch using a graph neural network (GNN) to model local correlations among body parts and the other branch modulating global frequencies for feature encoding. The paper includes ablation studies that assess the significance of various components, such as the GNN, the frequency modulation, and the window functions.

The existing ablation studies in the paper focus on the removal or alteration of key components like the GNN, the frequency modulation, and the window functions. However, there are potential areas for further exploration. One missing ablation could involve the specific choice of activation functions, such as the Sine function, which is crucial for frequency modulation. Another area could be the impact of the scaling factors used in the transformation of query points to bone-relative space, which could affect the processing efficiency and local pattern focus.

These additional ablation studies would help to further understand the contribution of these specific design choices to the overall performance of the method. The metrics used in the paper, such as PSNR, SSIM, and LPIPS, should be employed to evaluate the impact of these ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Activation Function
- **Ablated Part**: Sine activation function used in frequency modulation
- **Action**: REPLACE
- **Replacement**: 
  - ReLU
  - Tanh
  - LeakyReLU
- **Metrics**: PSNR, SSIM, LPIPS

### Ablation of Scaling Factors
- **Ablated Part**: Scaling factors in transformation to bone-relative space
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, LPIPS

</div>