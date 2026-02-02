# lm-planner/gpt-4o/spider-match

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "SpiderMatch: 3D Shape Matching with Global Optimality and Geometric Consistency" introduces a novel approach to 3D shape matching using a SpiderCurve representation and an integer linear programming (ILP) formulation. The key components of the method include the SpiderCurve representation, the ILP formulation with specific constraints (CYC, CON, PES, ANS), and the use of a cost function based on vertex-wise 3D shape features. To understand the contribution of each component to the overall performance, we can design ablation studies focusing on these elements.

1. **SpiderCurve Representation**: The SpiderCurve is a critical part of the method, as it discretizes the 3D shape into a long self-intersecting curve. Ablating this component by replacing it with alternative representations could reveal its importance in achieving geometric consistency and global optimality.

2. **ILP Constraints**: The constraints (CYC, CON, PES, ANS) ensure geometric consistency and the avoidance of new self-intersections. Ablating these constraints individually can help understand their specific contributions to the matching performance.

3. **Cost Function**: The cost function is based on vertex-wise 3D shape features. Modifying this function or using alternative features could provide insights into the sensitivity of the method to the choice of features.

4. **Solver Choice**: The paper uses the Gurobi solver for the ILP. Testing alternative solvers could help assess the impact of the solver choice on the efficiency and performance of the method.

5. **Feature Extraction Method**: The method uses a pretrained feature extractor for computing vertex-wise features. Replacing this with different feature extraction methods could show the dependency of the method on the quality of the features.

These ablation studies will help attribute the method's performance to its major components and understand the robustness and flexibility of the proposed approach.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: SpiderCurve Representation
- **Ablated Part**: SpiderCurve representation of the source 3D shape
- **Action**: REPLACE
- **Replacement**: 
  - Simple Curve
  - Mesh-based Representation
- **Metrics**: geometric_consistency, global_optimality, runtime

### Ablation 2: ILP Constraints
- **Ablated Part**: Individual ILP constraints (CYC, CON, PES, ANS)
- **Action**: REMOVE
- **Metrics**: geometric_consistency, global_optimality, runtime

### Ablation 3: Cost Function
- **Ablated Part**: Cost function based on vertex-wise 3D shape features
- **Action**: REPLACE
- **Replacement**: 
  - Euclidean Distance
  - Cosine Similarity
- **Metrics**: geometric_consistency, global_optimality, runtime

### Ablation 4: Solver Choice
- **Ablated Part**: Gurobi solver for ILP
- **Action**: REPLACE
- **Replacement**: 
  - CPLEX
  - GLPK
- **Metrics**: geometric_consistency, global_optimality, runtime

### Ablation 5: Feature Extraction Method
- **Ablated Part**: Pretrained feature extractor for vertex-wise features
- **Action**: REPLACE
- **Replacement**: 
  - Handcrafted Features
  - Deep Learning-based Features
- **Metrics**: geometric_consistency, global_optimality, runtime
</div>