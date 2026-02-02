<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/gangealing

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five high‐priority ablation studies that isolate the contributions of the major components in GAN-Supervised Dense Visual Alignment. First, we want to analyze the critical design choice in generating per-sample targets with style mixing: by varying the cutoff layer at which the latent vector switches from the learned target (p) to the random sample (w), we can study the trade-off between enforcing a common pose and preserving individual appearance. Second, since our spatial transformer is composed of a similarity transform followed by an unconstrained per-pixel flow, we propose an ablation that compares the performance of using each stage alone versus their composition. Third, we examine the parameterization of the target latent vector p: instead of optimizing it directly, we constrain it via a linear combination of the top-N principal directions. Testing different values of N (or even no PCA) can quantify how this reparameterization impacts alignment quality. Fourth, we focus on the regularizers (total variation and the identity transformation penalty) applied to the predicted flow. Removing them will reveal their role in ensuring smooth, well-behaved transformations. Finally, for datasets with high intra-class variation, our method extends to joint alignment and clustering using multiple target modes. Ablating this clustering component (e.g. comparing a single-mode versus multi-mode setup) can pinpoint its effect on dense correspondences. In all experiments, we propose reporting keypoint (PCK) accuracy and alignment loss as primary metrics; additional measurements (such as flow smoothness or classifier accuracy for clustering) are included where appropriate.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Style Mixing Cutoff Ablation
- **Ablated Part**: The fixed cutoff layer in style mixing used to construct per-sample targets (mix(p, w))
- **Action**: REPLACE
- **Replacement**: 
  - cutoff at layer 1
  - cutoff at layer 2
  - cutoff at layer 3
  - cutoff at layer 4
- **Metrics**: PCK, Alignment Loss

### Spatial Transformer Architecture Ablation
- **Ablated Part**: The composed Spatial Transformer network combining a similarity transformation and unconstrained per-pixel flow
- **Action**: REPLACE
- **Replacement**: 
  - Similarity-Only
  - Unconstrained-Only
  - Composed (default)
- **Metrics**: PCK, Alignment Loss

### Latent Vector Parameterization Ablation
- **Ablated Part**: The PCA-based reparameterization of the target latent vector p using top-N principal directions
- **Action**: REPLACE
- **Replacement**: 
  - Direct optimization (N=0)
  - PCA with N=5
  - PCA with N=10
  - PCA with N=20
- **Metrics**: PCK, Alignment Loss

### Regularization Ablation
- **Ablated Part**: The use of total variation and identity regularizers on the regressed flow field
- **Action**: REMOVE
- **Metrics**: PCK, Flow Smoothness, Alignment Loss

### Clustering Mechanism Ablation
- **Ablated Part**: The joint alignment and clustering component using multiple target latents and corresponding spatial transformers
- **Action**: REPLACE
- **Replacement**: 
  - Single-mode (K=1)
  - Multi-mode with K=3
  - Multi-mode with K=5
- **Metrics**: PCK, Cluster Assignment Accuracy

</div>