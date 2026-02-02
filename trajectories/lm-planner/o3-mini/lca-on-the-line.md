<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/lca-on-the-line

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose four key ablation experiments that target the core components of the LCA‐on‐the-Line framework. The first ablation removes the hierarchical signal completely to check if the rich taxonomy information is indeed essential for explaining OOD performance, comparing standard top-1 accuracies and effective robustness when the LCA distance is not computed. The second ablation replaces the method for constructing the class hierarchy. In the paper WordNet is used, but the authors also propose a K-means clustering based approach. Evaluating against alternatives (including a random or flat hierarchy) determines if the performance prediction robustness is sensitive to the taxonomy design. The third study focuses on how the function f(.) used in the LCA distance is defined. Since the distance is computed as f(y) minus f(N_LCA(y,y')), replacing f(.) with various candidates (tree depth, information content, or entropy) helps understand how the choice influences the correlation with OOD accuracy. Finally, the fourth ablation investigates taxonomy alignment techniques – that is, the additional alignment of model predictions with the class hierarchy using soft labels or prompt engineering. This study evaluates whether the extra alignment step is beneficial for both ID performance and OOD generalization, as measured by LCA distance and top-1 accuracies.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Remove Hierarchical Signal
- **Ablated Part**: Class taxonomy component used to compute LCA distance
- **Action**: REMOVE
- **Metrics**: ID Top-1 Accuracy, OOD Top-1 Accuracy, Effective Robustness (correlation between ID performance and OOD performance)

### Ablation 2: Alternative Taxonomy Construction
- **Ablated Part**: Method for constructing the class hierarchy
- **Action**: REPLACE
- **Replacement**: 
  - WordNet
  - K-means clustering-based taxonomy
  - Random/flat hierarchy
- **Metrics**: LCA Distance, OOD Top-1 Accuracy, Correlation between LCA Distance and OOD Accuracy

### Ablation 3: Varying Node Function f
- **Ablated Part**: Definition of the function f(.) in LCA distance computation
- **Action**: REPLACE
- **Replacement**: 
  - tree depth
  - information content
  - entropy
- **Metrics**: LCA Distance, OOD Top-1 Accuracy, Correlation with OOD Performance

### Ablation 4: Taxonomy Alignment Techniques
- **Ablated Part**: Approaches for aligning model predictions with the class taxonomy (e.g., soft label alignment or prompt engineering)
- **Action**: REPLACE
- **Replacement**: 
  - no alignment
  - soft label alignment
  - prompt engineering
- **Metrics**: ID Top-1 Accuracy, OOD Top-1 Accuracy, LCA Distance

</div>