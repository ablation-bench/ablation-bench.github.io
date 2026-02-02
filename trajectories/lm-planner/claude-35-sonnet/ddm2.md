<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/ddm2

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents a three-stage framework for MRI denoising:
1. Stage I: Noise model learning using self-supervised denoising
2. Stage II: Markov chain state matching
3. Stage III: Diffusion model training

The most critical components to ablate are:

1. The slice-wise processing approach vs volume-wise (this is a key innovation they highlight)
2. The noise shuffle operation in Stage III (this helps prevent the model from just learning to invert Stage I)
3. The J-Invariance optimization in Stage III (this modifies the loss function)
4. The statistical noise model calibration in Stage II (zero-mean adjustment)
5. The intermediate state matching approach vs starting from pure noise

These components represent the main technical contributions and design choices that differentiate their method from standard diffusion models and other denoising approaches.

The metrics used in the paper include:
- SNR (Signal-to-Noise Ratio)
- CNR (Contrast-to-Noise Ratio)
- Visual quality assessments
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Slice vs Volume Processing
- **Ablated Part**: Slice-wise processing scheme
- **Action**: REPLACE
- **Replacement**: 
  - volume-wise processing
  - patch-wise processing
- **Metrics**: SNR, CNR, inference time

### Noise Shuffle Ablation
- **Ablated Part**: Noise shuffle operation in Stage III
- **Action**: REMOVE
- **Metrics**: SNR, CNR

### Loss Function
- **Ablated Part**: J-Invariance optimization
- **Action**: REPLACE
- **Replacement**: 
  - standard MSE loss
  - L1 loss
- **Metrics**: SNR, CNR

### Noise Calibration
- **Ablated Part**: Zero-mean noise calibration in Stage II
- **Action**: REMOVE
- **Metrics**: SNR, CNR

### Sampling Strategy
- **Ablated Part**: Intermediate state matching
- **Action**: REPLACE
- **Replacement**: 
  - standard diffusion from pure noise
  - fixed intermediate state
- **Metrics**: SNR, CNR, inference time

</div>