<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/spider-match

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, the key components of SpiderMatch are:

1. The SpiderCurve representation of the source shape, which is created using a TSP approximation algorithm (Christofides).

2. The product graph construction between the SpiderCurve and target shape.

3. The constraints in the ILP formulation:
   - Cyclic Path (CYC)
   - Path Continuity (CON) 
   - Preservation of Existing Self-Intersections (PES)
   - Avoidance of New Self-Intersections (ANS)

4. The matching costs based on shape features.

The most important ablations should investigate:

1. The impact of the SpiderCurve representation by testing different curve generation methods
2. The necessity of each constraint type in the ILP formulation
3. The effect of different feature types for computing matching costs

I'll suggest the most critical ablations in order of importance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Constraint Ablation
- **Ablated Part**: ILP Constraints
- **Action**: REMOVE
- **Metrics**: geodesic error, runtime, geometric consistency

### SpiderCurve Generation
- **Ablated Part**: TSP approximation algorithm for SpiderCurve creation
- **Action**: REPLACE
- **Replacement**: 
  - random walk
  - shortest path
  - spectral ordering
- **Metrics**: geodesic error, runtime, surface coverage

### Feature Type
- **Ablated Part**: Shape features for matching costs
- **Action**: REPLACE
- **Replacement**: 
  - SHOT descriptors
  - heat kernel signatures
  - wave kernel signatures
- **Metrics**: geodesic error, runtime

### Self-Intersection Handling
- **Ablated Part**: Self-intersection constraints (PES and ANS)
- **Action**: REMOVE
- **Metrics**: geodesic error, geometric consistency, runtime

</div>