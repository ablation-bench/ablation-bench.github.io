<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/TIB__Detecting_Unknown_Objects_via_Two_Stream_Information_Bottleneck

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The proposed TIB method relies on two key components: the IB branch that compresses and enhances object-related features, and the RIB branch that generates simulative OOD features by reversing the bottleneck objective. Although the paper presents ablations for using only IB or RIB as well as the impact of the number of mixture branches and hyper-parameters, there remain important missing studies. One such missing study is to evaluate the necessity of the learned RIB branch. It is worthwhile to replace the RIB branch with a simple noise generator (e.g., Gaussian or uniform noise) so that we can quantify whether the performance gains stem from a learned simulative OOD feature extraction or are merely due to introducing random perturbations in the feature space. A second missing ablation is to investigate the effect of the choice of discrepancy loss used to maximize the prediction divergence between the enhanced ID features and the simulative OOD features. Currently, an absolute difference is used; however, other loss functions such as KL divergence or L2 loss could be experimented with to assess their impact on key metrics such as FPR95, AUROC, and mAP.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Replace RIB with Random Noise
- **Ablated Part**: Reverse Information Bottleneck (RIB) branch used for simulating OOD features
- **Action**: REPLACE
- **Replacement**: 
  - Gaussian noise
  - Uniform noise
- **Metrics**: FPR95, AUROC, mAP

### Ablation 2: Alternative Discrepancy Loss Functions
- **Ablated Part**: The loss function (Ldis) that maximizes the prediction discrepancy between the ID enhanced features and simulative OOD features
- **Action**: REPLACE
- **Replacement**: 
  - KL divergence
  - L2 loss
- **Metrics**: FPR95, AUROC, mAP

</div>