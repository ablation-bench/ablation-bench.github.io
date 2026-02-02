<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/3d-registration-with-maximal-cliques

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants a list of up to 5 important ablation studies for the paper "3D Registration with Maximal Cliques (MAC)". I need to identify the key components of the MAC method and propose ablations to understand their contribution to the overall performance.

Based on the abstract and method section (Section 3), the core components are:
1.  **Graph Construction:** Using either First Order Graph (FOG) or Second Order Graph (SOG).
2.  **Maximal Clique Search:** The key idea of using maximal cliques instead of just the maximum clique.
3.  **Clique Selection/Filtering:** Node-guided selection, normal consistency, and Top-K ranking.
4.  **Hypothesis Generation:** Using SVD (Instance-equal or Weighted).
5.  **Hypothesis Evaluation:** Using RANSAC-like metrics (MAE, MSE, Inlier Count).

The paper explicitly mentions comparing FOG vs. SOG and different hypothesis evaluation metrics in the ablation section (Sec. 4). The central claim is the benefit of using maximal cliques over the maximum clique. The clique selection/filtering and SVD weighting are also significant steps in the pipeline.

I will prioritize the ablations based on their impact on the core MAC concept and pipeline:

1.  **Maximal vs. Maximum Clique:** This directly tests the paper's main hypothesis.
2.  **Graph Construction:** Comparing FOG and SOG is a fundamental choice in the graph representation.
3.  **Clique Filtering (Top-K):** The number of hypotheses generated is crucial for both performance and efficiency. Ablating the Top-K selection shows its effect.
4.  **SVD Weighting:** This tests the impact of using graph-derived weights during transformation estimation.

The primary performance metrics used in the paper are Registration Recall, Rotation Error, and Translation Error. Runtime is also relevant for ablations affecting the number of hypotheses.

I will create four ablation studies covering these points, formatted as JSONL.

*   **Ablation 1:** Compare MAC (maximal cliques) against using only the maximum clique.
*   **Ablation 2:** Compare the two graph construction methods (SOG vs. FOG).
*   **Ablation 3:** Investigate the effect of the Top-K clique selection parameter.
*   **Ablation 4:** Compare the two SVD weighting schemes (Weighted vs. Instance-equal).

These four ablations cover the most critical aspects of the MAC method and align with typical ablation studies in this domain.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### MAC vs. Maximum Clique
- **Ablated Part**: Using maximal cliques for hypothesis generation
- **Action**: REPLACE
- **Replacement**: 
  - Using only the single maximum clique
- **Metrics**: Registration Recall, Rotation Error, Translation Error

### Graph Type Comparison
- **Ablated Part**: Second Order Graph (SOG) construction
- **Action**: REPLACE
- **Replacement**: 
  - First Order Graph (FOG)
- **Metrics**: Registration Recall, Rotation Error, Translation Error

### Effect of Top-K Clique Selection
- **Ablated Part**: Number of top-ranked maximal cliques selected (K)
- **Action**: REPLACE
- **Replacement**: 
  - Smaller K value
  - Larger K value
- **Metrics**: Registration Recall, Rotation Error, Translation Error, Runtime

### SVD Weighting Scheme
- **Ablated Part**: Weighted SVD using primary eigenvalues
- **Action**: REPLACE
- **Replacement**: 
  - Instance-equal SVD
- **Metrics**: Registration Recall, Rotation Error, Translation Error

</div>