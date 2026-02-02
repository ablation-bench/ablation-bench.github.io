<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/rgbd_semantic_segmentation_pytorch_mellable

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The following ablation studies aim to isolate and quantify the contributions of the main innovations in the paper. First, we assess the importance of learning a depth receptive field by replacing the differentiable softmax-based pixel assignment with a fixed, predefined one (similar to the standard 2.5D convolution). Next, we remove the kernel rebalancing weights that normalize the outputs of different kernels to examine their role in compensating for uneven pixel distributions. Further, we investigate how varying the number of 2D convolution kernels arranged along the depth-axis (e.g., using one versus multiple kernels) affects performance and computational cost. Finally, we test the sensitivity of the learned temperature parameter by fixing it to constant values, which can influence the sharpness of the soft assignment. The experiments are expected to be evaluated via segmentation metrics such as mean Intersection-over-Union (mIoU) and Pixel Accuracy (with additional computational metrics for kernel count variations).
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Fixed Depth Receptive Field
- **Ablated Part**: Learnable depth receptive field assignment (differentiable softmax-based pixel assigning)
- **Action**: REPLACE
- **Replacement**: 
  - fixed hard-threshold assignment as in conventional 2.5D convolution
- **Metrics**: mIoU, Pixel Accuracy

### Without Kernel Rebalancing
- **Ablated Part**: Kernel rebalancing weights used to scale outputs from different kernels
- **Action**: REMOVE
- **Metrics**: mIoU, Pixel Accuracy

### Varying Number of Kernels
- **Ablated Part**: Number of sequentially arranged 2D convolution kernels along the depth-axis
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 3
  - 5
- **Metrics**: mIoU, FLOPs, Params

### Fixed Temperature Parameter
- **Ablated Part**: Learnable temperature parameter controlling the sharpness of soft-assignment in receptive field functions
- **Action**: REPLACE
- **Replacement**: 
  - 0.5
  - 1.0
  - 2.0
- **Metrics**: mIoU, Pixel Accuracy

</div>