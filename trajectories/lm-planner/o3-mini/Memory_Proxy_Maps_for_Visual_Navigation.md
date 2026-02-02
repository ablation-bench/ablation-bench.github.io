<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Memory_Proxy_Maps_for_Visual_Navigation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper already conducts several ablation studies that focus on the choice of feature extractor for the high‐level memory proxy map (MPM) and on the hierarchical combination of modules (MPM, mid-level WayNet, and low-level worker). However, two important analyses appear to be missing. First, while the paper uses an isomap imitator network to project high-dimensional SMoG features into a 2D latent space for the MPM, it does not investigate whether this specific choice is critical. A missing ablation study could replace the isomap imitator with alternative dimensionality reduction techniques (e.g., PCA, UMAP) or even bypass the projection step to directly use the SMoG feature distances. This experiment would clarify how sensitive navigation performance (using metrics such as Success Rate and SPL) is to the choice of dimensionality reduction in building an interpretable memory representation. 

Second, the method relies on multiple confidence thresholds (αc, αk, αm) and a visitation ratio (ψ) for keypoint matching and updating the MPM. These hyperparameters are empirically set, yet their influence on the downstream navigation performance is not studied. A study that varies these thresholds across a range of values (for instance, testing values like 0.5, 0.7, and 0.9 for the α parameters and alternatives for ψ) would provide valuable insight into the robustness and sensitivity of the overall approach.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A: Isomap Imitator Replacement
- **Ablated Part**: Isomap imitator network that maps SMoG features to a 2D memory proxy map
- **Action**: REPLACE
- **Replacement**: 
  - PCA-based dimensionality reduction
  - UMAP-based dimensionality reduction
  - Direct usage of high-dimensional SMoG features without projection
- **Metrics**: Success Rate, SPL

### Ablation B: Confidence Threshold Sensitivity
- **Ablated Part**: Confidence threshold parameters (αc, αk, αm, and visitation ratio ψ) used for keypoint matching and MPM updates
- **Action**: REPLACE
- **Replacement**: 
  - α thresholds: 0.5, 0.7, 0.9; ψ: 0.7, 0.85, 1.0
- **Metrics**: Success Rate, SPL

</div>