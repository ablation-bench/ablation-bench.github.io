<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/lca-on-the-line

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, the key components that warrant ablation studies are:

1. The choice of class hierarchy (WordNet vs K-means clustering) is fundamental to the method, as it affects how LCA distance is calculated.

2. The LCA distance calculation method itself, which measures hierarchical distance between predictions and ground truth.

3. The alignment of model predictions with class taxonomies through soft labels or prompt engineering.

4. The evaluation across different types of models (VMs vs VLMs) and datasets.

5. The correlation analysis between LCA distance and OOD performance.

I'll suggest ablations focusing on these key components, ranked by importance:
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Hierarchy Source Ablation
- **Ablated Part**: WordNet class hierarchy
- **Action**: REPLACE
- **Replacement**: 
  - K-means clustering hierarchy
  - Random hierarchy
  - Flat hierarchy
- **Metrics**: LCA distance, OOD top-1 accuracy, ID top-1 accuracy

### LCA Distance Metric Ablation
- **Ablated Part**: LCA distance calculation method
- **Action**: REPLACE
- **Replacement**: 
  - Tree depth
  - Path length
  - Information content
- **Metrics**: OOD top-1 accuracy, ID LCA distance

### Model Alignment Ablation
- **Ablated Part**: Taxonomy alignment method
- **Action**: REPLACE
- **Replacement**: 
  - Soft labels
  - Prompt engineering
  - No alignment
- **Metrics**: LCA distance, OOD top-1 accuracy

### Dataset Distribution Ablation
- **Ablated Part**: ImageNet OOD variants
- **Action**: REPLACE
- **Replacement**: 
  - ImageNet-A
  - ImageNet-R
  - ImageNet-S
  - ObjectNet
- **Metrics**: LCA distance correlation, OOD top-1 accuracy

### Model Type Impact
- **Ablated Part**: Model architecture type
- **Action**: REPLACE
- **Replacement**: 
  - Vision Models only
  - VLMs only
  - Mixed VMs and VLMs
- **Metrics**: LCA-OOD correlation coefficient, ID-OOD accuracy correlation

</div>