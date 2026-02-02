<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/spider-match

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants to identify key components of the SpiderMatch method and propose up to 5 ablation studies, ranked by importance. The method's core contributions are the SpiderCurve representation, the formulation as an Integer Linear Program (ILP) on a product graph, and novel constraints within the ILP to ensure geometric consistency and global optimality.

Based on the paper's description, the most critical components appear to be:
1.  The geometric consistency constraints: Preservation of Existing Self-Intersections (PES) and Avoidance of New Self-Intersections (ANS). These are explicitly introduced to guarantee geometric consistency, a key claim.
2.  The ILP formulation itself, which allows integrating these constraints and solving for global optimality.
3.  The SpiderCurve representation, which transforms the 3D-3D matching into a path-based problem on a product graph.
4.  The matching cost function, which guides the shortest path search.

Ablation studies should target these components.

-   **Ablating Constraints:** Removing the geometric consistency constraints (PES and ANS) is the most direct way to test their impact on geometric consistency and overall performance. Removing them together provides a strong baseline. Removing them individually (ANS only, PES only) offers more granular insight into the role of each type of constraint.
-   **Ablating the ILP Formulation:** Replacing the ILP with a simpler shortest path algorithm (like Dijkstra on the product graph without constraints) would be a significant change, but it's not a simple 'REMOVE' or 'REPLACE' of a *part* within the existing framework. The paper argues the ILP is necessary *because* of the constraints.
-   **Ablating the SpiderCurve:** Modifying the SpiderCurve extraction (e.g., using a simpler path, varying density) is possible but less clearly defined as a simple ablation within the described method, which emphasizes covering all vertices using a TSP approximation.
-   **Ablating Matching Costs:** The cost function uses specific features and a robust loss. Replacing the robust loss with a standard L2 loss is a feasible ablation.

Prioritizing based on the paper's emphasis and the clarity of defining the ablation:
1.  Removing the geometric consistency constraints (PES and ANS) is paramount as it directly tests the core novel contribution for geometric consistency.
2.  Removing the ANS constraint individually tests the role of preventing new intersections.
3.  Removing the PES constraint individually tests the role of preserving existing intersections.
4.  Replacing the robust loss function tests the impact of the specific cost formulation.

These four ablations cover the most critical and clearly defined aspects of the ILP formulation and cost function. The metrics used in the paper for evaluation include geodesic error (for matching accuracy) and runtime. These should be reported for the ablation studies.

The plan is to propose four ablation studies:
1.  Remove both PES and ANS constraints.
2.  Remove only the ANS constraint.
3.  Remove only the PES constraint.
4.  Replace the robust loss in the cost function with L2 loss.

These will be formatted as JSONL objects with the specified fields and ranked by importance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Geometric Consistency Constraints
- **Ablated Part**: Geometric consistency constraints (PES and ANS) in the ILP
- **Action**: REMOVE
- **Metrics**: Geodesic error, Runtime

### No Avoidance of New Intersections
- **Ablated Part**: Avoidance of New Self-Intersections (ANS) constraint in the ILP
- **Action**: REMOVE
- **Metrics**: Geodesic error, Runtime

### No Preservation of Existing Intersections
- **Ablated Part**: Preservation of Existing Self-Intersections (PES) constraint in the ILP
- **Action**: REMOVE
- **Metrics**: Geodesic error, Runtime

### L2 Matching Cost
- **Ablated Part**: Robust loss function (Barron's loss) in the matching cost calculation
- **Action**: REPLACE
- **Replacement**: 
  - L2 loss
- **Metrics**: Geodesic error, Runtime

</div>