<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/mixup-amp

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants a list of up to 5 ablation studies for the paper "Adversarial Mixing Policy for Relaxing Locally Linear Constraints in Mixup". I need to identify the key components of the proposed method (AMP) and suggest modifications or removals to understand their contribution to the overall performance. The output must be in a specific JSONL format, ranked by importance, and use metrics mentioned in the paper.

Based on the abstract and methodology section:
1.  **Core Idea:** AMP adds a small *adversarial* perturbation ($\nabla \lambda$) to the mixing coefficient ($\lambda$) and uses this perturbed coefficient ($\lambda'$) *only* for the synthetic example, while keeping the original $\lambda$ for the synthetic label. This is the mechanism for injecting "slight non-linearity".
2.  **Mechanism:** The perturbation is calculated via gradient ascent on the Mixup loss w.r.t. $\lambda$ (MaxOp).
3.  **Optimization:** The final loss minimized is selected via a mask, choosing the larger loss between the original Mixup loss (using $\lambda$ for both) and the loss using the perturbed example (with $\lambda'$) and original label (with $\lambda$) (MinOp).
4.  **Hyperparameters:** Key hyperparameters include $\varepsilon$ (perturbation step size) and $\alpha$ (Beta distribution parameter).

Potential Ablations (ranked by importance):

1.  **Remove the core AMP mechanism:** Compare AMP to the baseline Mixup (no perturbation). This is essential to show if AMP provides any benefit at all.
2.  **Test the "perturb example only" aspect:** Instead of perturbing only the example's mixing coefficient, perturb both the example's and the label's mixing coefficients. This tests if the specific way AMP injects non-linearity is crucial.
3.  **Test the "adversarial" aspect:** Replace the adversarial perturbation with a random perturbation of the same magnitude. This tests if the direction of the perturbation matters.
4.  **Test the MinOp mask:** Remove the mask and always minimize the loss using the perturbed example/original label pair. This tests the importance of the loss selection strategy.
5.  **Test sensitivity to $\varepsilon$:** Vary the step size $\varepsilon$ for the adversarial perturbation. This is a key hyperparameter and its impact should be understood.

The paper emphasizes "error rate" as the primary metric and highlights performance in "low-resource conditions". "Error Rate" will be the metric used.

I will create 5 JSON objects corresponding to these ablations, formatted as requested.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Baseline Mixup
- **Ablated Part**: Adversarial perturbation and MinOp loss selection mechanism
- **Action**: REMOVE
- **Metrics**: Error Rate

### AMP - Perturb Example & Label
- **Ablated Part**: Applying perturbation only to example mixing coefficient
- **Action**: REPLACE
- **Replacement**: 
  - Apply perturbation to both example and label mixing coefficients
- **Metrics**: Error Rate

### AMP - Random Perturbation
- **Ablated Part**: Adversarial perturbation calculation
- **Action**: REPLACE
- **Replacement**: 
  - Random perturbation of magnitude epsilon
- **Metrics**: Error Rate

### AMP - No Loss Mask
- **Ablated Part**: MinOp loss selection mask
- **Action**: REMOVE
- **Metrics**: Error Rate

### AMP - Vary Epsilon
- **Ablated Part**: Perturbation step size epsilon
- **Action**: REPLACE
- **Replacement**: 
  - 0.01
  - 0.05
  - 0.1
  - 0.2
  - 0.5
- **Metrics**: Error Rate

</div>