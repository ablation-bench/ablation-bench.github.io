<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Reformer__A_Deep_Learning_Model_for_Runtime_Selection_of_Convolution_Kernels

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper already compares the overall performance of the Γ‑block versus traditional transformer blocks and demonstrates the benefits of the Reformer model in terms of training/inference times and kernel selection speedup. However, two crucial components of the proposed method have not been individually ablated. First, the Γ‑block uses a dual‐path architecture where one pathway processes the input through a nonlinear transformation (via a fully connected network and affine projection) and the other bypasses this with a direct affine mapping. An ablation study that removes one of these pathways would directly assess the contribution of the dual-path design to accuracy and runtime improvements. Second, the paper introduces a novel ratio‑preserving probability formulation for training the network to predict optimal kernels based on their runtimes. Although the paper discusses alternatives like one‑hot encoding and softmax probabilities in Table 2, it does not show an ablation comparing these different target formulations. Replacing the ratio‑preserving probabilities with one‑hot or softmax variants would clarify the effectiveness of the proposed approach in mitigating sensitivity to runtime noise.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Dual-Path Architecture in Γ-block
- **Ablated Part**: Dual-path structure within the Γ-block, specifically the additional nonlinear processing pathway that complements the direct affine projection.
- **Action**: REMOVE
- **Metrics**: Train Accuracy, Test Accuracy, Training Time, Inference Time, Convolution Kernel Speedup

### Ablation on Ground-Truth Probability Formulation
- **Ablated Part**: The method for generating target probability distributions for kernel selection (using ratio-preserving probabilities) instead of standard one-hot encoding.
- **Action**: REPLACE
- **Replacement**: 
  - one-hot
  - softmax
  - ratio-preserving
- **Metrics**: Kernel Selection Accuracy, Average Convolution Runtime, Speedup

</div>