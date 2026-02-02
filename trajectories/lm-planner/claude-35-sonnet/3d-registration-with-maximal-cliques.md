<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/3d-registration-with-maximal-cliques

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, the MAC method has several key components that warrant investigation through ablation studies:

1. Graph Construction: The paper uses two approaches (First Order Graph and Second Order Graph) to construct the compatibility graph. This is a fundamental choice that affects the entire pipeline.

2. Clique Selection Strategy: The method uses node-guided clique selection with weight-based filtering. This is a crucial component that determines which maximal cliques are used for registration.

3. SVD Variants: The paper mentions two variants for transformation estimation - Instance-equal SVD and Weighted SVD.

4. Normal Consistency Filter: This is used as an additional filtering technique for maximal cliques.

5. Hypothesis Evaluation Metrics: Different metrics (MAE, MSE, inlier count) are used for evaluating hypotheses.

I'll suggest ablation studies for the most important components that would help understand their contribution to the method's performance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Graph Construction Ablation
- **Ablated Part**: Graph construction method
- **Action**: REPLACE
- **Replacement**: 
  - First Order Graph (FOG)
  - Second Order Graph (SOG)
- **Metrics**: Registration Recall, Rotation Error (RE), Translation Error (TE)

### Clique Selection Strategy Ablation
- **Ablated Part**: Node-guided clique selection with weight filtering
- **Action**: REPLACE
- **Replacement**: 
  - Random clique selection
  - Size-based selection (largest cliques)
  - Weight-only selection (without node guidance)
- **Metrics**: Registration Recall, Rotation Error (RE), Translation Error (TE)

### SVD Variant Ablation
- **Ablated Part**: SVD algorithm variant for transformation estimation
- **Action**: REPLACE
- **Replacement**: 
  - Instance-equal SVD
  - Weighted SVD
- **Metrics**: Registration Recall, Rotation Error (RE), Translation Error (TE)

### Normal Consistency Filter Ablation
- **Ablated Part**: Normal consistency filtering for maximal cliques
- **Action**: REMOVE
- **Metrics**: Registration Recall, Rotation Error (RE), Translation Error (TE)

</div>