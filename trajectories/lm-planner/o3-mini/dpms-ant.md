<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/dpms-ant

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies targeting the core components of DPMs-ANT. The first ablation removes the similarity-guided training strategy that leverages a pre-trained classifier to steer the noise correction during transfer. This will help reveal how much the classification-based guidance contributes to image quality and training stability. The second ablation removes the adversarial noise selection mechanism, replacing it with the conventional, non-adaptive Gaussian noise schedule, to evaluate its effect on overfitting, diversity, and overall performance. The third ablation studies the adaptor module, which is used to efficiently bridge the gap between the pre-trained source model and the target domain. Removing this module tests its contribution to enabling effective transfer in few-shot settings. The fourth ablation replaces the fixed number of inner gradient ascent steps (used to compute the “worse-case” noise) with several candidate values. This will assess the sensitivity of the model’s performance to the iterations used for adversarial noise selection. Finally, the fifth ablation tunes the hyperparameter gamma that scales the similarity-guided noise correction term. Testing different gamma values will clarify its impact on convergence and the balance between source and target alignment. For all experiments, metrics such as FID, LPIPS, training iterations/stability, and diversity or convergence rate are proposed to gauge performance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Similarity Guidance Removal
- **Ablated Part**: similarity-guided training strategy that leverages a pre-trained classifier to guide noise correction
- **Action**: REMOVE
- **Metrics**: FID, LPIPS, Training Iterations

### Adversarial Noise Removal
- **Ablated Part**: adversarial noise selection mechanism that dynamically selects targeted noise based on input images
- **Action**: REMOVE
- **Metrics**: FID, LPIPS, Diversity

### Adaptor Module Ablation
- **Ablated Part**: adaptor module that bridges the pre-trained model and the target domain
- **Action**: REMOVE
- **Metrics**: FID, LPIPS, Training Stability

### Adversarial Noise Iterations Sensitivity
- **Ablated Part**: the number of inner gradient ascent steps in adversarial noise selection
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 3
  - 5
  - 10
- **Metrics**: FID, LPIPS, Training Stability

### Gamma Weight Tuning
- **Ablated Part**: the hyperparameter gamma scaling the similarity-guided noise correction term
- **Action**: REPLACE
- **Replacement**: 
  - 0
  - 0.5
  - 1.0
  - 2.0
- **Metrics**: FID, LPIPS, Convergence Rate

</div>