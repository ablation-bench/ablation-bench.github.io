<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/spider-match

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose a set of five ablation studies targeting the core elements of SpiderMatch. First, to assess the impact of preserving the self-intersections of the SpiderCurve, Ablation A will remove the coupling constraints (PES) in the ILP that enforce identical treatment of intersecting vertices. In Ablation B, we remove the avoidance of new self-intersections constraints (ANS) to quantify how vital they are for preventing spurious correspondences. Since the SpiderCurve is a novel representation generated using the Christofides TSP approximation and vertex duplication, Ablation C will replace the extraction method with alternative strategies (e.g., nearest neighbor TSP, randomized traversal, or geodesic spanning tree) to measure changes in coverage and matching quality. Ablation D focuses on the cost function: SpiderMatch uses a robust loss (as in Barron 2019) to compute matching costs between 3D features, and we propose testing simpler alternatives (e.g., L2 norm, L1 norm, or Huber loss) to assess the sensitivity of the final matching to the particular cost formulation. Finally, Ablation E studies the ILP optimization itself by replacing (or relaxing) the integer constraints with continuous relaxations and rounding strategies, to understand trade-offs between global optimality guarantees and runtime improvements. In all experiments, we will report standard metrics used in the paper such as matching accuracy, geometric consistency error, runtime, and additional indicators (e.g. surface coverage or objective function value) where appropriate.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A: Removal of Coupling Constraints
- **Ablated Part**: Coupling constraints (PES) that preserve existing self-intersections in the SpiderCurve
- **Action**: REMOVE
- **Metrics**: matching accuracy, geometric consistency error, runtime

### Ablation B: Removal of New Intersection Avoidance
- **Ablated Part**: Constraints (ANS) that prevent the introduction of new self-intersections during matching
- **Action**: REMOVE
- **Metrics**: matching accuracy, geometric consistency error, false correspondence rate, runtime

### Ablation C: SpiderCurve Extraction Method Replacement
- **Ablated Part**: The SpiderCurve extraction algorithm (currently using Christofides TSP with vertex duplication) for discretizing the source 3D shape
- **Action**: REPLACE
- **Replacement**: 
  - Christofides TSP
  - Nearest Neighbor TSP
  - Randomized Traversal
  - Geodesic Spanning Tree
- **Metrics**: surface coverage, matching accuracy, geometric consistency error, runtime

### Ablation D: Matching Cost Function Replacement
- **Ablated Part**: The robust loss function used to compute matching costs between 3D features
- **Action**: REPLACE
- **Replacement**: 
  - L2 norm
  - L1 norm
  - Huber loss
- **Metrics**: matching accuracy, objective function value, geometric consistency error

### Ablation E: ILP to Continuous Relaxation
- **Ablated Part**: The integer constraints in the ILP formulation that guarantee global optimality
- **Action**: REPLACE
- **Replacement**: 
  - Exact ILP
  - Continuous Relaxation with Rounding
- **Metrics**: matching accuracy, optimality gap, runtime

</div>