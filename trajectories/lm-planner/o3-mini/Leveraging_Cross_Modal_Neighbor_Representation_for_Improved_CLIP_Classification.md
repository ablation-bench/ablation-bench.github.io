<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Leveraging_Cross_Modal_Neighbor_Representation_for_Improved_CLIP_Classification

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Our analysis indicates that while the paper thoroughly investigates the benefits of CODER and the APG module through various prompt types and dimensionality reduction techniques, it misses two important ablation studies. First, although the authors emphasize the importance of dense sampling in constructing the CODER, they do not analyze the sensitivity of performance to the number of neighbor texts (K) used in its construction. Varying K could reveal the optimal balance between representation richness and computational overhead in both zero-shot and few-shot settings. Second, the paper consistently uses cosine similarity as the distance metric in constructing CODER without exploring if it is the best option. An ablation study comparing cosine similarity with alternate distance metrics (e.g., Euclidean, Manhattan, or even a learnable metric) could help further justify this design choice. Both ablations are crucial as they address core components of the method that directly influence the quality of the feature representation and classification performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Neighbor Text Count Ablation
- **Ablated Part**: The number of APG-generated text samples (K) used to construct the CODER
- **Action**: REPLACE
- **Replacement**: 
  - 10
  - 25
  - 50
  - 100
- **Metrics**: zero-shot accuracy, few-shot accuracy

### Distance Metric Ablation
- **Ablated Part**: The cosine similarity metric used to compute image-text distances in CODER
- **Action**: REPLACE
- **Replacement**: 
  - Euclidean
  - Manhattan
  - Learnable MLP-based metric
- **Metrics**: zero-shot accuracy, few-shot accuracy

</div>