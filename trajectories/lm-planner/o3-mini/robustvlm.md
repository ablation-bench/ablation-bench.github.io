<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/robustvlm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose four ablation studies that target the core components of the unsupervised adversarial fine‐tuning scheme. First, we assess the importance of the feature preservation constraint by removing the loss term that forces the robust encoder’s output to stay close to the original CLIP embedding. This ablation will show how essential preserving clean performance is for downstream zero‐shot tasks and LVLM behavior under adversarial attacks. Second, we vary the perturbation radius (ε) used in the inner maximization during fine‐tuning by testing different values (e.g. 1/255, 2/255, 4/255). This will help us understand the trade-off between robustness and clean performance. Third, we replace the L2 distance in the unsupervised adversarial loss with a cosine similarity loss. This ablation examines whether the choice of metric for measuring embedding deviation affects the preservation of CLIP’s semantic content and downstream performance. Fourth, we introduce a weighting hyperparameter in the loss to trade off the feature preservation term against adversarial robustness. By testing several values (e.g. 0.5, 1.0, 2.0), we aim to quantify whether a softer constraint might better balance robust and clean accuracy. These carefully ranked ablations will isolate the contributions of each design choice.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Remove Feature Preservation Constraint
- **Ablated Part**: The unsupervised loss that enforces the robust encoder’s output to remain close to the original CLIP embedding (L2 difference between φ(z) and φ_org(x)).
- **Action**: REMOVE
- **Metrics**: zero-shot classification accuracy, robust classification accuracy under ℓ∞ attacks, downstream task performance (e.g., image captioning and VQA)

### Ablation 2: Vary Perturbation Radius
- **Ablated Part**: The fixed perturbation radius (ε) used during the inner maximization for generating adversarial examples in fine-tuning.
- **Action**: REPLACE
- **Replacement**: 
  - 1/255
  - 2/255
  - 4/255
- **Metrics**: clean performance on zero-shot tasks, robust performance under ℓ∞ attacks, LVLM task performance

### Ablation 3: Loss Function Variation
- **Ablated Part**: The distance metric in the unsupervised adversarial loss function used to measure the deviation between φ(z) and φ_org(x).
- **Action**: REPLACE
- **Replacement**: 
  - L2 loss
  - cosine similarity loss
- **Metrics**: cosine similarity deviation, zero-shot classification accuracy, robust classification accuracy, downstream task performance (e.g., VQA, image captioning)

### Ablation 4: Introduce Loss Weighting Factor
- **Ablated Part**: The implicit equal weighting of the feature preservation loss in the adversarial fine-tuning objective.
- **Action**: ADD
- **Replacement**: 
  - 0.5
  - 1.0
  - 2.0
- **Metrics**: trade-off between clean and robust performance, zero-shot classification accuracy, LVLM downstream performance

</div>