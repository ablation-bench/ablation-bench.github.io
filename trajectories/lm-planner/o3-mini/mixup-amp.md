<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/mixup-amp

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose four ablation studies to investigate the contribution of each critical component of AMP. First, by removing the adversarial perturbation (the Max operation) we can assess the benefit of relaxing the strict linear constraints when compared to standard Mixup – essentially isolating the effect of the adversarial injection. Second, we test the sensitivity of the method to the step size (ε) used to perturb the mixing coefficient by replacing its default value with several alternatives (including zero, which is equivalent to no perturbation), to determine the optimal perturbation strength. Third, we investigate the loss selection mechanism in the Min operation: the original design uses a mask to choose between the loss on the original and the perturbed mixing coefficient. Replacing this mask-based selection with alternative strategies (such as averaging the two losses or even choosing the lower loss) can reveal the importance of this design choice. Fourth, we replace the adversarial gradient-based perturbation with random noise (sampled from uniform or Gaussian distributions) to verify that the adversarial direction indeed contributes to the AMP’s regularization effect rather than just any stochastic perturbation. In all these studies, classification error rate, accuracy, and F1 score (the metrics used in the paper’s evaluations on text classification) are measured.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Remove Adversarial Perturbation
- **Ablated Part**: Max operation that injects adversarial perturbation into the mixing coefficient
- **Action**: REMOVE
- **Metrics**: error_rate, accuracy, F1_score

### Ablation 2: Sensitivity to Perturbation Magnitude
- **Ablated Part**: Step size parameter (ε) controlling the magnitude of the adversarial perturbation in the Max operation
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.05
  - 0.1
  - 0.2
- **Metrics**: error_rate, accuracy, F1_score

### Ablation 3: Loss Selection Strategy
- **Ablated Part**: Mask-based loss selection mechanism in the Min operation that chooses between the original loss and the perturbed loss
- **Action**: REPLACE
- **Replacement**: 
  - average_loss (mean of the two losses)
  - minimum_loss (select lower loss)
- **Metrics**: error_rate, accuracy, F1_score

### Ablation 4: Replace Adversarial Perturbation with Random Noise
- **Ablated Part**: Perturbation injection mechanism on the mixing coefficient
- **Action**: REPLACE
- **Replacement**: 
  - uniform random noise
  - Gaussian random noise
- **Metrics**: error_rate, accuracy, F1_score

</div>