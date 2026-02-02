<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/deviant

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The DEVIANT paper introduces a novel approach to monocular 3D object detection by incorporating depth equivariance into the network architecture. The key innovation is the use of scale equivariant steerable blocks to achieve depth equivariance, which is not present in traditional vanilla convolutional networks. The paper claims that this approach leads to improved depth estimation and better generalization across datasets.

To design meaningful ablation studies, we should focus on the core components that contribute to the claimed improvements. These include the use of scale equivariant steerable blocks, the handling of depth translations, and the overall architecture modifications that support these features. The goal of the ablation studies is to isolate the impact of these components on the performance metrics used in the paper, such as 3D detection accuracy on the KITTI and Waymo datasets.

1. Ablation of Scale Equivariant Steerable Blocks: This is the most critical component of the DEVIANT architecture. By replacing these blocks with vanilla convolutions, we can assess their direct impact on the network's performance.

2. Ablation of Depth Equivariance: This involves testing the network's performance without the depth equivariance feature, possibly by using a different method to handle depth translations or by disabling the depth equivariance mechanism.

3. Ablation of 3D Pooling and Batch Normalization: The paper mentions the use of 3D pooling and batch normalization to handle the additional scale dimension. Testing the network with 2D pooling and batch normalization can reveal the importance of these modifications.

4. Comparison with Log-Polar Convolution: The paper discusses the limitations of log-polar convolution due to discretization issues. An ablation study could involve implementing log-polar convolution to empirically validate these claims.

5. Cross-Dataset Evaluation: The paper claims improved generalization across datasets. An ablation study could involve training on one dataset and testing on another to quantify this generalization capability.

These ablation studies will help in understanding the contribution of each component to the overall performance of the DEVIANT network.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Scale Equivariant Steerable Blocks
- **Ablated Part**: Scale equivariant steerable blocks
- **Action**: REPLACE
- **Replacement**: 
  - Vanilla convolution
- **Metrics**: AP_3D, AP_BEV, AP_2D

### Ablation of Depth Equivariance
- **Ablated Part**: Depth equivariance mechanism
- **Action**: REMOVE
- **Metrics**: AP_3D, AP_BEV, AP_2D

### Ablation of 3D Pooling and Batch Normalization
- **Ablated Part**: 3D pooling and batch normalization
- **Action**: REPLACE
- **Replacement**: 
  - 2D pooling
  - 2D batch normalization
- **Metrics**: AP_3D, AP_BEV, AP_2D

### Comparison with Log-Polar Convolution
- **Ablated Part**: Scale equivariant steerable blocks
- **Action**: REPLACE
- **Replacement**: 
  - Log-polar convolution
- **Metrics**: AP_3D, AP_BEV, AP_2D

### Cross-Dataset Evaluation
- **Ablated Part**: Training and testing datasets
- **Action**: ADD
- **Replacement**: 
  - Train on KITTI, test on Waymo
  - Train on Waymo, test on KITTI
- **Metrics**: AP_3D, AP_BEV, AP_2D

</div>