<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/owod

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The proposed ablation studies focus on isolating and validating the contributions of the key components of the proposed ORE method. First, removing the contrastive clustering module will reveal its importance in enforcing discriminative separation in the latent feature space, which is central to both accurate unknown detection and robust incremental learning. Next, since the energy‐based unknown identifier is a novel component that distinguishes unknowns via Helmholtz free energy, replacing it with standard alternatives (e.g., softmax thresholding or MC-Dropout) will help quantify its benefits. Third, the auto-labelling mechanism—leveraging RPN proposals to label potential unknowns—is a practical heuristic; removing it will highlight its role in providing supervision for unknowns without manual annotation. Fourth, the exemplar replay strategy for mitigating catastrophic forgetting is a simpler yet critical component in incremental learning; ablating it will show how much the replay helps preserve performance on previously learned classes. Finally, studying the sensitivity of the prototype momentum parameter in the contrastive clustering module (by testing several values) will help understand how this hyperparameter influences the quality of the learned feature clusters. These ablations are prioritized by their potential impact on the method’s overall performance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Contrastive Clustering Removal
- **Ablated Part**: Contrastive clustering module that enforces latent space feature separation via prototype management and contrastive loss
- **Action**: REMOVE
- **Metrics**: mAP, Unknown Detection Rate, Incremental mAP

### Ablation 2: Energy-Based Unknown Identifier Replacement
- **Ablated Part**: Energy-based unknown identification head that uses the Helmholtz free energy formulation
- **Action**: REPLACE
- **Replacement**: 
  - Standard softmax thresholding
  - MC-Dropout uncertainty estimation
- **Metrics**: mAP, Unknown Detection Rate, Open-set Detection Accuracy

### Ablation 3: Auto-Labelling Unknowns Removal
- **Ablated Part**: Auto-labelling mechanism for unknown objects using high-scoring RPN proposals
- **Action**: REMOVE
- **Metrics**: mAP, Unknown Detection Rate, False Positive Rate on Unknowns

### Ablation 4: Exemplar Replay Removal
- **Ablated Part**: Exemplar replay strategy used to mitigate catastrophic forgetting during incremental learning
- **Action**: REMOVE
- **Metrics**: Incremental mAP, Forgetting Rate

### Ablation 5: Prototype Momentum Sensitivity
- **Ablated Part**: Momentum parameter used for updating class prototypes in contrastive clustering
- **Action**: REPLACE
- **Replacement**: 
  - 0.5
  - 0.7
  - 0.9
- **Metrics**: mAP, Cluster Separation Metric, Unknown Detection Rate

</div>